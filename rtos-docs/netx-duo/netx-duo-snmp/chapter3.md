---
title: Kapitel 3 – Beskrivning Azure RTOS för NetX Duo SNMP-agenttjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SNMP Agent-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b24776c2eb25a53195ea4eb452497b23b933e4ab3f9f0a379ea64d8469c1c971
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790130"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>Kapitel 3 – Beskrivning Azure RTOS för NetX Duo SNMP-agenttjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo SNMP-agenttjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *Ange autentiseringsnyckel (endast SNMP v3) för trap-meddelanden*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *Ange autentiseringsnyckel (endast SNMP v3) för svarsmeddelanden*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *Hämta communitynamn*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *Ange kontextmotor (endast SNMP v3)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *Ange kontextnamn (endast SNMP v3)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *Skapa SNMP-agent*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *Hämta SNMP-versionen av det mottagna paketet*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *Ange om den senaste SNMP-begäran är GET- eller SET-typ*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *Kontrollera om strängen matchar agentens privata sträng*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *Kontrollera om strängen matchar agentens offentliga sträng*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *Ange nätverksgränssnitt för SNMP-meddelanden*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *Ange strängen för den privata communityn för SNMP-agenten*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *Ange den offentliga community-strängen för SNMP-agenten*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *Ange SNMP-agentstatus för alla SNMP-versioner*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *Ta bort SNMP-agent*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *Skapa md5-nyckel (endast SNMP v3)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *Skapa md5-nyckel (endast SNMP v3)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *Ange krypteringsnyckel (endast SNMP v3) för trap-meddelanden*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *Ange krypteringsnyckel (endast SNMP v3) för svarsmeddelanden*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *Skapa sha-nyckel (endast SNMP v3)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *Skapa sha-nyckel (endast SNMP v3)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *Starta SNMP-agenten*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *Stoppa SNMP-agenten*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *Skicka SNMP v1-trap (endast IPv4)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *Skicka SNMP v2-trap (endast IPv4)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *Skicka SNMP v2-trap (endast IPv4) och ange OID*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *Skicka SNMP v3-trap (endast IPv4)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *Skicka SNMP v2-trap (endast IPv4) och ange OID*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *Skicka SNMP v1-trap (IPv4 och IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *Skicka SNMP v2-trap (IPv4 och IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *Skicka SNMP v2-trap (IPv4/IPv6) och ange OID*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *Skicka SNMP v3-trap (IPv4 och IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *Skicka SNMP v2-trap (IPv4/IPv6) och ange OID*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *Ange antalet omstarter*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *Jämföra två objekt*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *Jämföra två objekt*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *Kopiera ett objekt*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *Kopiera ett objekt*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *Hämta räknarobjekt*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *Ange räknarobjekt*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *Hämta 64-bitars räknarobjekt*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *Ange 64-bitars räknarobjekt*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *Ange värdet för end-of-mib*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *Hämta mätarobjekt*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *Ange mätarobjekt*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *Hämta objekt-ID*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *Ange objekt-ID*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *Hämta heltalsobjekt*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *Ange heltalsobjekt*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *Hämta IP-adressobjekt (endast IPv4)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *Ange IP-adressobjekt (endast IPv4)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *Hämta IP-adressobjekt (endast IPv6)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *Ange IP-adressobjekt (endast IPv6)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *Ange no-instance-värde*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *Ange värde som inte hittades*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *Hämta oktettsträngsobjekt*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *Ange oktettsträngsobjekt*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *Hämta ASCII-strängobjekt*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *Ange ASCII-strängobjekt*
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - *Hämta timetics-objekt*
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - *Ange timetics-objekt*

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
Ange autentiseringsnyckel för trap-meddelanden

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Description

Den här tjänsten anger den nyckel som ska användas för att ange autentiseringsparametrar i SNMPv3-säkerhetshuvudet i trap-meddelanden. Om du NX_NULL ett värde för nyckeln inaktiveras autentiseringen.

> [!NOTE]
> Nyckeln måste skapas tidigare. Se nx_snmp_agent_md5_key_create eller nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **nyckel** Pekare till en tidigare skapad MD5- eller SHA-nyckel.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad autentiseringsnyckeluppsättning.
- **NX_NOT_ENABLED** (0x14) SNMP Security inaktiverat 
- **NX_PTR_ERROR** (0x07) Ogiltig SNMP-agent pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
Ange autentiseringsnyckel för svarsmeddelanden

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Description

Den här tjänsten anger nyckeln som ska användas för autentiseringsparametrar i säkerhetsparametern SNMPv3 för alla begäranden som görs när den har angetts. Om du NX_NULL ett värde för nyckeln inaktiveras autentiseringen.

> [!NOTE]
> Nyckeln måste skapas tidigare. Se nx_snmp_agent_md5_key_create eller nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **nyckel** Pekare till en tidigare skapad MD5- eller SHA-nyckel.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-nyckeluppsättning.
- **NX_NOT_ENABLED** (0x14) SNMP Security inaktiverat
- **NX_PTR_ERROR** (0x07) Ogiltig SNMP-agent pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
Hämta communitynamn

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar gruppnamnet från den senaste SNMP-begäran som tagits emot av SNMP-agenten.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **community_string_ptr** Pekare till en sträng pekare för att returnera SNMP Agent community-strängen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-community get.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
Ange om den senaste SNMP-begäran är GET- eller SET-typ

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>Description

Den här tjänsten anger om den senaste begäran från SNMP Manager är av typen GET (GET, GETNEXT eller GETBULK) eller SET. Den är avsedd att användas med motringning av användarnamn där SNMPv1- eller SNMPv2-programmet vill jämföra den mottagna community-strängen med den offentliga SNMP-agentsträngen om begäran är en GET-typ, eller med den privata SNMP-agentsträngen om begäran är en SET-typ.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **is_get_type** Pekare till status för begärandetyp:  
NX_TRUE get-typ  
NX_FALSE om SET-typ

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Returnerad typ
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
Ange kontextmotor (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Description

Den här tjänsten anger kontextmotorn för SNMP-agenten. Det gäller endast för SNMPv3-bearbetning. Detta bör anropas innan du skapar säkerhetsnycklar om programmet använder autentisering och kryptering, eftersom kontextmotorns ID används i processen för att skapa nycklar. Om inte, tillhandahåller NetX Duo SNMP ett standardkontextmotor-ID överst *i nxd_snmp.c:*

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **context_engine** Pekare till kontextmotorsträngen.
- **context_engine_size** Storlek på kontextmotorsträngen. Observera att det maximala antalet byte i en kontextmotor definieras av NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-kontextmotoruppsättning.
- **NX_NOT_ENABLED** (0x14) SNMPv3 är inte aktiverat
- **NX_SNMP_ERROR** (0x100) Kontextmotorstorleksfel.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
Ange kontextnamn (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Description

Den här tjänsten anger kontextnamnet för SNMP-agenten. Det gäller endast för SNMPv3-bearbetning. Om det inte anropas lämnar NetX Duo SNMP-agenten kontextnamnet tomt.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **context_name** Pekare till kontextnamnssträngen.
- **context_name_size** Storlek på kontextnamnssträngen. Observera att det maximala antalet byte i ett kontextnamn definieras av NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-kontextnamnuppsättning.
- **NX_SNMP_ERROR** (0x100) Storleksfel för kontextnamn.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
Skapa SNMP-agent

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a>Description

Den här tjänsten skapar en SNMP-agent på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **snmp_agent_name** Pekare till SNMP-agentens namnsträng.
- **ip_ptr** Pekare till IP-instans.
- **stack_ptr** Pekare till SNMP-agentens trådstack pekare.
- **stack_size** Stackstorlek i byte.
- **pool_ptr** Pekare på standardpaketpoolen för den här SNMP-agenten.
- **snmp_agent_username_process** Funktions pekare till programmets användarnamnshanteringsrutin.
- **snmp_agent_get_process** Funktions pekare till programmets get-begärandehanteringsrutin.
- **snmp_agent_getnext_process** Funktionspekare till programmets getnext-hanteringsrutin för förfrågningar.
- **snmp_agent_set_process** Funktions pekare till programmets hanteringsrutin för SET-begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Skapa SNMP-agenten.
- **NX_SNMP_ERROR** (0x100) SNMP Agent create error (Skapa SNMP-agent).
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a>nx_snmp_agent_current_version_get
Hämta SNMP-paketversionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den SNMP-version som parsats från det senaste mottagna SNMP-paketet.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **version** Pekare till SNMP-versionen som parsats från det mottagna SNMP-paketet

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-version hämta
- **NX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a>nx_snmp_agent_private_string_test
Kontrollera att den privata strängen matchar agentens privata sträng

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Description

Den här tjänsten jämför den null-avslutade indata-community-strängen med den privata strängen för SNMP-agenten och anger om de matchar.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **community_string** Pekare till sträng att jämföra
- **is_private** Pekare till jämförelseresultat  
NX_TRUE – strängmatchning  
NX_FALSE – strängen matchar inte

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad jämförelse
- **NX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a>nx_snmp_agent_public_string_test
Kontrollera att den mottagna offentliga strängen matchar agentens offentliga sträng

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Description

Den här tjänsten jämför en null-avslutad indata-community-sträng med den offentliga strängen för SNMP-agenten och anger om de matchar.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **community_string** Pekare till sträng att jämföra
- **is_public** Pekare till jämförelseresultat  
NX_TRUE – strängmatchning  
NX_FALSE – strängen matchar inte

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad jämförelse
- **NX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a>nx_snmp_agent_version_set
Ange SNMP-agentstatus för varje SNMP-version

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Description

Den här tjänsten anger status (aktiverad/inaktiverad) för var och en av SNMP-versionerna, V1, V2 och V3 på SNMP-agenten. Observera att de användarkonfigurerbara alternativen, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 och NX_SNMP_DISABLE_V3, åsidosätter dessa körningsinställningar. Som standard är SNMP-agenten aktiverad för alla tre versionerna.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **enabled_v1** Anger aktiverad status för SNMP V1 till på/av.
- **enabled_v2** Anger aktiverad status för SNMP V2 till på/av.
- **enabled_v3** Anger aktiverad status för SNMP V3 till på/av.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-versionsuppsättning
- **NX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a>nx_snmp_agent_private_string_set
Ange den privata strängen för SNMP-agenten

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Description

Den här tjänsten anger den privata community-strängen för SNMP-agenten med den null-avslutade indatasträngen. Standardvärdet är NULL (ingen privat stränguppsättning), så att alla SNMP-paket som tas emot med en "privat" community-sträng inte godkänns av SNMP-agenten för läs-/skrivåtkomst. Indatasträngen måste vara mindre än eller lika med användaren som kan konfigureras NX_SNMP_MAX_USER_NAME-1 (för att tillåta utrymme för null-avslutning).

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **community_string** Pekare till den privata sträng som ska tilldelas

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har angett privat sträng
- **NX_SNMP_ERROR_TOOBIG** (0x01) Strängstorlek för stor 
- **NX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a>nx_snmp_agent_public_string_set
Ange offentlig sträng för SNMP-agenten

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>Description

Den här tjänsten anger den offentliga community-strängen för SNMP-agenten med den null-avslutade indatasträngen. Community-strängen måste vara mindre än eller lika med användaren som kan konfigureras NX_SNMP_MAX_USER_NAME-1 (för att tillåta utrymme för null-avslutning).

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **community_string** Pekare till den offentliga sträng som ska tilldelas

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har angett offentlig sträng
- **NX_SNMP_ERROR_TOOBIG** (0x01) Strängstorlek för stor
- **NX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a>nx_snmp_agent_delete
Ta bort SNMP-agent

### <a name="prototype"></a>Prototyp

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad SNMP-agent.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Borttagning av SNMP-agenten.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
Ange SNMP-agentens nätverksgränssnitt

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Description

Den här tjänsten anger SNMP-nätverksgränssnittet för SNMP-agenten enligt inmatningsgränssnittets index. Detta är endast användbart för SNMP-värdprogram med NetX Duo 5.6 eller senare som stöder flera nätverksgränssnitt. Standardvärdet om det inte anges av värden är noll för det primära gränssnittet.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **If_index** Index som anger SNMP-gränssnittet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-gränssnittsuppsättning.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
Skapa md5-nyckel (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Description

Den här tjänsten skapar en MD5-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_snmp_agent_md5_key_create_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **lösenord** Pekare till lösenordssträng.
- **destination_key** Pekare till SNMP-nyckeldatastrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades nyckel skapas.
- **NX_NOT_ENABLED** (0x14) Säkerhet är inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
Skapa md5-nyckel (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>Description

Den här tjänsten skapar en MD5-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten *ersätter nx_snmp_agent_md5_key_create().* Den här versionen kräver att anroparen tillhandahåller lösenordslängd.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **lösenord** Pekare till lösenordssträng.
- **password_length** Längd på lösenordssträng.
- **destination_key** Pekare till SNMP-nyckeldatastrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades nyckel skapas.
- **NX_NOT_ENABLED** (0x14) Säkerhet är inte aktiverat.
- **NX_SNMP_FAILED** (0x102) SNMP misslyckades.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
Ange krypteringsnyckel för trap-meddelanden

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Description

Den här tjänsten anger att en tidigare skapad sekretessnyckel ska användas för kryptering och dekryptering av SNMPv3-trapmeddelanden.

> [!NOTE]
> *En autentiseringsnyckel måste skapas tidigare. SNMP v3-sekretess (kryptering) kräver autentisering. Se nx_snmp_agent_auth_trap_key_use för mer information.*

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **nyckel** Pekare till tidigare skapa nyckel.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad sekretessnyckeluppsättning.
- **NX_NOT_ENABLED** (0x14) Säkerhet är inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
Ange krypteringsnyckel för svarsmeddelanden

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Description

Den här tjänsten anger att den tidigare skapade nyckeln ska användas för kryptering och dekryptering av SNMPv3-svarsmeddelanden.

> [!NOTE]
> *En autentiseringsnyckel måste ha angetts tidigare. SNMP v3-kryptering kräver även att en autentiseringsnyckel skapas. Se nx_snmp_agent_authentiation_key_use för mer information.*

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **nyckel** Pekare till tidigare skapa nyckel.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad sekretessnyckeluppsättning.
- **NX_NOT_ENABLED** (0x14) Säkerhet är inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
Skapa SHA-nyckel (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>Description

Den här tjänsten skapar en SHA-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_snmp_agent_sha_key_create_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **lösenord** Pekare till lösenordssträng.
- **destination_key** Pekare till SNMP-nyckeldatastrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades nyckel skapas.
- **NX_SNMP_ERROR** (0x100) Skapa nyckel.
- **NX_PTR_ERROR** (0x07) Ogiltig SNMP-agent eller nyckel pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
Skapa SHA-nyckel (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>Description

Den här tjänsten skapar en SHA-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten *ersätter nx_snmp_agent_sha_key_create().* Den här versionen kräver att anroparen tillhandahåller lösenordslängd.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **lösenord** Pekare till lösenordssträng.
- **password_length** Längd på lösenordssträng.
- **destination_key** Pekare till SNMP-nyckeldatastrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades nyckel skapas.
- **NX_SNMP_ERROR** (0x100) Skapa nyckel.
- **NX_SNMP_FAILED** (0x102) Det gick inte att skapa nyckeln.
- **NX_PTR_ERROR** (0x07) Ogiltig SNMP-agent eller nyckel pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
Starta SNMP-agenten 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Description

Den här tjänsten binder UDP-socketen till SNMP-port 161 och startar SNMP Agent-tråduppgiften.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad start av SNMP-agenten.
- **NX_SNMP_ERROR** (0x100) SNMP-agentens startfel.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
Stoppa SNMP-agenten 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Description

Den här tjänsten stoppar SNMP Agent-agentens trådaktivitet och tar bort bindningarna för UDP-socketen till SNMP-porten.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad stopp av SNMP-agenten.
- **NX_PTR_ERROR** (0x07) Ogiltig SNMP-agent pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
Skicka SNMPv1-trap *(endast IPv4)*

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar en SNMP-trap till SNMP Manager på den angivna IPv4-adressen. Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att *använda nxd_snmp_agent_trap_send tjänsten.* *nx_snmp_agent_trap_send* ingår i NetX Duo för att stödja befintliga NetX SNMP Agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IPv4-adressen för SNMP Manager.
- **enterprise** Enterprise-objekt-ID-sträng (sysObectID).
- **trap_type** Typ av trap som begärs enligt följande:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** Specifik trapkod.
- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trap-skicka.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_NOT_ENABLED** (0x14) SNMPv1 inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a>nxd_snmp_agent_trap_send
Skicka SNMPv1-trap *(IPv4 och IPv6)*

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMP-trap till SNMP Manager på den angivna IP-adressen. Motsvarande metod för att skicka en SNMP-trap i NetX är *nxd_snmp_agent_trap_send tjänsten.*

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IPv4- eller IPv6-adress för SNMP Manager.
- **enterprise** Enterprise-objekt-ID-sträng (sysObectID).
- **trap_type** Typ av trap som begärs enligt följande:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** Specifik trapkod.
- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trap-skicka.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_NOT_ENABLED** (0x14) SNMPv1 inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a>nx_snmp_agent_trapv2_send
Skicka SNMPv2-trap (endast IPv4)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMPv2-trap till SNMP Manager på den angivna IPv4-adressen. Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att *använda nxd_snmp_agent_trapv2_send tjänsten.* *nx_snmp_agent_trapv2_send* ingår i NetX Duo för att stödja befintliga NetX SNMP Agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IPv4-adressen för SNMP Manager.
- **community** Communitynamn (användarnamn).
- **trap_type**  
   Typ av trap som begärts. Standardhändelserna är:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   För upphovsrättsskyddade data:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras *i nxd_snmp.h*)
   
- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_NOT_ENABLED** (0x14) SNMPv2 inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a>nx_snmp_agent_trapv2_oid_send
Skicka SNMPv2-trap som anger OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMPv2-trap till SNMP Manager på den angivna IP-adressen (endast IPv4) och tillåter anroparen att ange OID direkt. Den bästa metoden för att skicka en SNMP-trap med angiven OID i NetX Duo är att *använda nxd_snmp_agent_trapv2_oid_send tjänsten.* *nx_snmp_agent_trapv2_oid_ i* NetX Duo för att stödja befintliga NetX SNMP Agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IP-adress för SNMP Manager.
- **community** Gruppnamn (användarnamn).
- **oid** Pekare till buffert som innehåller OID.
- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_PTR_ERROR** (0x16) Ogiltig SNMP-agent eller parameterpekare.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-måladress.
- **NX_OPTION_ERROR** (0x0a) Ogiltig parameter.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a>nxd_snmp_agent_trapv2_send
Skicka SNMPv2-trap (IPv4 och IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMP V2-trap till SNMP Manager på den angivna IP-adressen.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IP-adressen (IPv4 eller IPv6) för SNMP Manager.
- **community** Gruppnamn (användarnamn).
- **trap_type**  
   Typ av trap som begärdes. Standardhändelserna är:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   För upphovsrättsskyddade data:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras *i nxd_snmp.h*)

- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_NOT_ENABLED** (0x14) SNMPv2 inte aktiverat.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) IP-version som inte stöds
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a>nxd_snmp_agent_trapv2_oid_send
Skicka SNMPv2-trap som anger OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMP v2-trap till SNMP Manager på den angivna IP-adressen (IPv4/IPv6) och gör att anroparen kan ange OID direkt.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IP-adress för SNMP Manager (IPv4/IPv6).
- **community** Gruppnamn (användarnamn).
- **oid** Pekare till buffert som innehåller OID.
- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_PTR_ERROR** (0x16) Ogiltig SNMP-agent eller parameterpekare.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-måladress.
- **NX_OPTION_ERROR** (0x0a) Ogiltig parameter.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a>nx_snmp_agent_trapv3_send
Skicka SNMPv3-trap (endast IPv4)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar en SNMPv3-trap till SNMP Manager på den angivna IPv4-adressen. Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att *använda nxd_snmp_agent_trapv3_send tjänsten.* *nx_snmp_agent_trapv3_send* ingår i NetX Duo för att stödja befintliga NetX SNMP Agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IPv4-adressen för SNMP Manager.
- **användarnamn** Gruppnamn (användarnamn).
- **trap_type**  
   Typ av trap som begärdes. Standardhändelserna är:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   För upphovsrättsskyddade data:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras *i nxd_snmp.h*)

- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_NOT_ENABLED** (0x14) SNMPv3 inte aktiverat.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a>nx_snmp_agent_trapv3_oid_send
Skicka SNMPv3-trap som anger OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMPv3-trap till SNMP Manager på den angivna IP-adressen (endast IPv4) och tillåter anroparen att ange OID direkt. Den bästa metoden för att skicka en SNMP-trap med angiven OID i NetX Duo är att *använda nxd_snmp_agent_trapv3_oid_send-tjänsten.* *nx_snmp_agent_trapv3_oid_ i* NetX Duo för att stödja befintliga NetX SNMP Agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IP-adress för SNMP Manager.
- **användarnamn** Gruppnamn (användarnamn).
- **oid** Pekare till buffert som innehåller OID.
- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_PTR_ERROR** (0x16) Ogiltig SNMP-agent eller parameterpekare.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-måladress.
- **NX_OPTION_ERROR** (0x0a) Ogiltig parameter.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a>nxd_snmp_agent_trapv3_send
Skicka SNMPv3-trap (IPv4 och IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMP-trap till SNMP Manager på den angivna IP-adressen. Den här trapen är i princip samma som SNMP v2-trapen, förutom att trapmeddelandeformatet finns i PDU för SNMP v3.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** IP-adressen (IPv4 eller IPv6) för SNMP Manager.
- **användarnamn** Gruppnamn (användarnamn).
- **trap_type**  
   Typ av trap som begärdes. Standardhändelserna är:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   För upphovsrättsskyddade data:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras *i nxd_snmp.h*)

- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_NOT_ENABLED** (0x14) SNMPv3 inte aktiverat.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) IP-version som inte stöds
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a>nxd_snmp_agent_trapv3_oid_send
Skicka SNMPv3-trap som anger OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Description

Den här tjänsten skickar en SNMPv3-trap till SNMP Manager på den angivna IP-adressen (IPv4/IPv6) och tillåter anroparen att ange OID:n direkt.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP-agentkontrollblocket.
- **ip_address** Pekare till IP-adressen för SNMP Manager.
- **användarnamn** Användarnamn (communitynamn).
- **oid** Pekare till buffert som innehåller OID.
- **elapsed_time** Tidssystemet har varit upp (sysUpTime).
- **object_list_ptr** Matris med objekt och deras associerade värden som ska ingå i SNMP-trapen. Listan är NX_NULL avslutad.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad SNMP-trapssändning.
- **NX_SNMP_ERROR** (0x100) Fel vid sändning av SNMP-trap.
- **NX_PTR_ERROR** (0x16) Ogiltig SNMP-agent eller parameterpekare.
- **NX_IP_ADDRESS_ERROR** (0x21) Ogiltig IP-måladress.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a>nx_snmp_agent_v3_context_boots_set
Ange antalet omstarter (om SNMPv3 är aktiverat)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>Description

Den här tjänsten anger antalet omstarter som registreras av SNMP-agenten. Den här tjänsten är endast tillgänglig om SNMPv3 har aktiverats för SNMP-agenten eftersom startantal endast används i SNMPv3-protokollet.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till SNMP Agent-kontrollblock
- **boots** Värdet för att ange startantalet för SNMP-agenten till

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Antal start har angetts
- **NX_SNMP_ERROR** (0x100) Fel vid startantal
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a>nx_snmp_object_compare
Jämföra två objekt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Description

Den här tjänsten jämför det angivna objekt-ID:t med referensobjekt-ID:t. Båda objekt-ID:erna finns i ASCII SMI-notationen. Båda objekten måste t.ex. börja med ASCII-strängen "1.3.6".

Den här tjänsten är inaktuell. Utvecklare uppmuntras att migrera till *nx_snmp_object_compare_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **objekt** Pekare till objekt-ID.
- **reference_object** Pekare till referensobjektets ID.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Objektet matchar referensobjektet.
- **NX_SNMP_NEXT_ENTRY** (0x101) Objektet är mindre än referensobjektet.
- **NX_SNMP_ERROR** (0x100) Objektet är större än referensobjektet.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a>nx_snmp_object_compare_extended
Jämföra två objekt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Description

Den här tjänsten jämför det angivna objekt-ID:t med referensobjekt-ID:t. Båda objekt-ID:erna finns i ASCII SMI-notationen. Båda objekten måste t.ex. börja med ASCII-strängen "1.3.6".

Den här tjänsten *ersätter nx_snmp_object_compare().* Den här versionen kräver att anropare tillhandahåller längdinformation.

### <a name="input-parameters"></a>Indataparametrar

- **request_object** Pekare för att begära objekt-ID.
- **request_object_length** Längden på objekt-ID:t för begäran.
- **reference_object** Pekare till referensobjektets ID.
- **reference_object_length** Längden på referensobjektets ID.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Objektet matchar referensobjektet.
- **NX_SNMP_NEXT_ENTRY** (0x101) Objektet är mindre än referensobjektet.
- **NX_SNMP_ERROR** (0x100) Objektet är större än referensobjektet.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a>nx_snmp_object_copy
Kopiera ett objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a>Description

Den här tjänsten kopierar källobjektet i ASCII SIM-notationen till målobjektet.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_snmp_object_copy_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **source_object_name** Pekare till källobjekt-ID.
- **destination_object_name** Pekare till målobjekt-ID.

### <a name="return-values"></a>Returvärden

- **storlek** Antal byte som kopierats till målnamnet. Om felet returneras noll.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a>nx_snmp_object_copy_extended
Kopiera ett objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten kopierar källobjektet i ASCII SIM-notationen till målobjektet.

Den här tjänsten *ersätter nx_snmp_object_copy().* Den här versionen kräver att anropare tillhandahåller längdinformation.

### <a name="input-parameters"></a>Indataparametrar

- **source_object_name** Pekare till källobjekt-ID.
- **source_object_name_length** Längden på källobjektets ID.
- **destination_object_name_buffer** Pekare till målobjektbufferten.
- **destination_object_name_buffer_size** Storleken på målobjektbufferten.

### <a name="return-values"></a>Returvärden

- **storlek** Antal byte som kopierats till målnamnet. Om felet returneras noll.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a>nx_snmp_object_counter_get
Hämta räknarobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Description

Den här tjänsten hämtar räknarobjektet på adressen som anges av käll pekaren och placerar det i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till räknarkälla.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Räknarobjektet har hämtats.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
Ange räknarobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger räknaren på den adress som anges av mål pekaren med räknarvärdet i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till räknarmål.
- **object_data** Pekare till räknarens källobjektsstruktur.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Räknarobjektet har ställts in.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
Hämta 64-bitars räknarobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar 64-bitars räknarobjektet på adressen som anges av käll pekaren och placerar det i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till räknarkälla.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Räknarobjektet har hämtats.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
Ange 64-bitars räknarobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Description

Den här tjänsten anger 64-bitarsräknaren på adressen som anges av mål pekaren med räknarvärdet i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till räknarmål.
- **object_data** Pekare till räknarens källobjektsstruktur.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Räknarobjektet har ställts in.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
Ange värdet för end-of-mib 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten skapar ett objekt som signalerar slutet av MIB och anropas vanligtvis från get- eller GETNEXT-programmets motringningsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **not_used_ptr** Pekaren används inte – bör NX_NULL.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Objektet end-of-mib har skapats.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
Hämta mätarobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar mätarobjektet på adressen som anges av käll pekaren och placerar det i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till mätarkälla.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Mätarobjektet har hämtats.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
Ange mätarobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger mätaren på den adress som anges av mål pekaren med mätarvärdet i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till mätarmål.
- **object_data** Pekare till mätarkällans objektstruktur.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Mätarobjektet har ställts in.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
Hämta objekt-ID 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar objekt-ID:t (i ASCII SIM-notation) på adressen som anges av källpekaren och placerar det i NetX-objektdatastrukturen. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till objekt-ID-källa.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Objekt-ID:t har hämtats.
- **NX_SNMP_ERROR** (0x100) Ogiltig längd på objekt
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
Ange objekt-ID 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger objekt-ID :t (i ASCII SIM-notation) på adressen som anges av mål pekaren med objekt-ID:t i NetX-objektdatastrukturen. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till objekt-ID-mål.
- **object_data** Pekare till objektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Objekt-ID har angetts.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
Hämta heltalsobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar heltalsobjektet på adressen som anges av käll pekaren och placerar det i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till heltalskälla.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Heltalsobjektet har hämtats.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
Ange heltalsobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger heltal på den adress som anges av mål pekaren med heltalsvärdet i NetX-objektdatastrukturen. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till heltalsmål.
- **object_data** Pekare till objektstrukturen för heltalskällan.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Heltalsobjektet har ställts in.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
Hämta IP-adressobjekt (endast IPv4)

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar IP-adressobjektet på adressen som anges av käll pekaren och placerar det i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till IPv4-adresskälla.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IP-adressobjektet har hämtats.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
Hämta IP-adressobjekt (endast IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar IPv6-adressobjektet på adressen som anges av käll pekaren och placerar det i NetX-objektets datastruktur.
Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till IPv6-adresskälla.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IP-adressobjektet har hämtats.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Felaktig SNMP-objektkod för indata
- **NX_NOT_ENABLED** (0x14) IPv6 inte aktiverat
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
Ange IPv4-adressobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger IPv4-adressen på den adress som anges av mål pekaren med IP-adressen i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till IP-adress som ska anges.
- **object_data** Pekare till OBJEKTstruktur för IP-adress.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IP-adressobjektet har angetts.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
Ange IPv6-adressobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger IPv6-adressen på den adress som anges av mål pekaren med IP-adressen i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till IP-adress som ska anges.
- **object_data** Pekare till OBJEKTstruktur för IP-adress.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IPv6-adressen har angetts.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_NOT_ENABLED** (0x14) IPv6 inte aktiverat
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
Ange no-instance-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten skapar ett -objekt som signalerar att det inte fanns någon instans av det angivna objektet och anropas vanligtvis från callbackrutinen för GET- eller GETNEXT-programmet.

### <a name="input-parameters"></a>Indataparametrar

- **not_used_ptr** Pekaren används inte – bör NX_NULL.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) No-instance-objektet har skapats.
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
Ange objekt som inte hittades 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten skapar ett objekt som signalerar att objektet inte hittades och anropas vanligtvis från get- eller GETNEXT-programmets motringningsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **not_used_ptr** Pekaren används inte – bör NX_NULL.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Det hittades inte-objektet har skapats.
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
Hämta oktettsträngsobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Description

Den här tjänsten hämtar oktettsträngen på adressen som anges av käll pekaren och placerar den i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till oktettsträngkälla.
- **object_data** Pekare till målobjektstrukturen.
- **längd** Antal byte i oktettsträngen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Oktettsträngobjektet har hämtats.
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
Ange oktettsträngsobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger oktettsträngen på adressen som anges av mål pekaren med oktettsträngen i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till målet för oktettsträngen.
- **object_data** Pekare till objektstrukturen för oktettsträngens källobjekt.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Oktettsträngobjektet har angetts.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
Hämta ASCII-strängobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar ASCII-strängen på adressen som anges av käll pekaren och placerar den i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till ASCII-strängkälla.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) ASCII-strängobjektet har hämtats.
- **NX_SNMP_ERROR** (0x100) Strängen är för stor  
- **NX_PTR_ERROR** (0x07) Ogiltig indata pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
Ange ASCII-strängobjekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger ASCII-strängen på adressen som anges av mål pekaren med ASCII-strängen i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till ASCII-strängmål.
- **object_data** Pekare till ASCII-strängkällans objektstruktur.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) ASCII-strängobjektet har ställts in.
- **NX_SNMP_ERROR** (0x100) Sträng för stor.
- **NX_SNMP_ERROR_BADVALUE** (0x03) Ogiltigt tecken i sträng
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
Hämta timetics-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten hämtar tidsinformationen på den adress som anges av käll pekaren och placerar den i NetX-objektets datastruktur. Den här rutinen anropas vanligtvis från get- eller GETNEXT-programanropsrutinen.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till timetics-källa.
- **object_data** Pekare till målobjektstrukturen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Timetics-objektet har hämtats.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
Ange timetics-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

Den här tjänsten anger tidsvariabeln för den adress som anges av mål pekaren med tidstics i NetX-objektdatastrukturen.
Den här rutinen anropas vanligtvis från set-programmets återanropsrutin.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till timetics-målet.
- **object_data** Pekare till objektstrukturen för timetics-källan.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Timetics-objektet har angetts.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Ogiltig objekttyp.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```