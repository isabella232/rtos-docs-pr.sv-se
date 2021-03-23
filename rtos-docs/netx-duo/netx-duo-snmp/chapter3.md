---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNMP agent-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SNMP agent-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825767"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNMP agent-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo SNMP agent-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *Ange autentiseringsnyckel (endast SNMP v3) för trap-meddelanden*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *Ange autentiseringsnyckel (endast SNMP v3) för svarsmeddelanden*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *Hämta community-namn*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *Ange kontext motor (endast SNMP v3)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *Ange kontext namn (endast SNMP v3)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *Skapa SNMP-agent*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *Hämta SNMP-versionen av det mottagna paketet*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *Ange om den senaste SNMP-begäran är GET-eller SET-typ*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *Avgöra om strängen matchar agentens privata sträng*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *Avgöra om strängen matchar den offentliga agentens sträng*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *Ange nätverks gränssnitt för SNMP-meddelanden*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *Ange SNMP-agentens privata grupp sträng*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *Ange SNMP-agentens offentliga grupp sträng*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *Ange SNMP-agentens status för alla SNMP-versioner*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *Ta bort SNMP-agent*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *Skapa en MD5-nyckel (endast SNMP v3)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *Skapa en MD5-nyckel (endast SNMP v3)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *Ange krypterings nyckel (endast SNMP v3) för trap-meddelanden*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *Ange krypterings nyckel (endast SNMP v3) för svarsmeddelanden*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *Skapa SHA-nyckel (endast SNMP v3)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *Skapa SHA-nyckel (endast SNMP v3)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *Starta SNMP-agenten*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *Stoppa SNMP-agenten*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *Skicka SNMP v1 Trap (endast IPv4)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *Skicka SNMP v2 Trap (endast IPv4)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *Skicka SNMP v2 Trap (endast IPv4) ange OID*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *Skicka SNMP v3 Trap (endast IPv4)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *Skicka SNMP v2 Trap (endast IPv4) ange OID*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *Skicka SNMP v1-Trap (IPv4 och IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *Skicka SNMP v2-Trap (IPv4 och IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *Skicka SNMP v2 Trap (IPv4/IPv6) som anger OID*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *Skicka SNMP v3 Trap (IPv4 och IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *Skicka SNMP v2 Trap (IPv4/IPv6) som anger OID*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *Ange antal omstarter*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *Jämför två objekt*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *Jämför två objekt*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *Kopiera ett objekt*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *Kopiera ett objekt*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *Hämta räknar objekt*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *Ange Counter-objekt*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *Hämta 64-bitars räknar objekt*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *Ange 64-bit Counter-objekt*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *Ange värdet för slut punkt för MIB*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *Hämta mätar objekt*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *Ange mätar objekt*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *Hämta objekt-ID*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *Ange objekt-ID*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *Hämta heltals objekt*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *Ange heltals objekt*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *Hämta IP-adress-objekt (endast IPv4)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *Ange IP-adress-objekt (endast IPv4)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *Hämta IP-adress-objekt (endast IPv6)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *Ange IP-adress-objekt (endast IPv6)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *Ange inget-instans värde*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *Värdet hittades inte*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *Hämta oktett-String-objekt*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *Ange oktett-String-objekt*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *Hämta ASCII-String-objekt*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *Ange ASCII-String-objekt*
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
### <a name="description"></a>Beskrivning

Den här tjänsten anger den nyckel som ska användas för att ställa in autentiseringsmetoder i säkerhets huvudet SNMPv3 i trap-meddelanden. Om du anger ett NX_NULL-värde för nyckeln inaktive ras autentiseringen.

> [!NOTE]
> Nyckeln måste ha skapats tidigare. Se nx_snmp_agent_md5_key_create eller nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **nyckel** Pekare till en tidigare skapad MD5-eller SHA-nyckel.

### <a name="return-values"></a>Retur värden

- Den angivna nyckeln för **NX_SUCCESS** (0x00) har angetts.
- **NX_NOT_ENABLED** (0X14) SNMP-säkerhet inaktive rad 
- **NX_PTR_ERROR** (0X07) ogiltig SNMP-agent pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

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
### <a name="description"></a>Beskrivning

Den här tjänsten anger den nyckel som ska användas för autentiseringsmetoder i säkerhets parametern SNMPv3 för alla begär Anden som görs när den har angetts. Om du anger ett NX_NULL-värde för nyckeln inaktive ras autentiseringen.

> [!NOTE]
> Nyckeln måste ha skapats tidigare. Se nx_snmp_agent_md5_key_create eller nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **nyckel** Pekare till en tidigare skapad MD5-eller SHA-nyckel.

### <a name="return-values"></a>Retur värden

- Den SNMP-nyckel som **NX_SUCCESS** (0X00) lyckades.
- **NX_NOT_ENABLED** (0X14) SNMP-säkerhet inaktive rad
- **NX_PTR_ERROR** (0X07) ogiltig SNMP-agent pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
Hämta community-namn

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar community-namnet från den senaste SNMP-begäran som tagits emot av SNMP-agenten.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **community_string_ptr** Pekare till en sträng pekare som returnerar SNMP-agentens grupp sträng.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SNMP community get.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
Ange om den senaste SNMP-begäran är GET-eller SET-typ

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger om den senaste begäran från SNMP-hanteraren är en GET-, GETNEXT-eller GETBULK-eller SET-typ. Den är avsedd att användas med det användar namn för användar namn som används för att jämföra den mottagna grupp strängen med den offentliga SNMP-agenten om begäran är en GET-typ eller till en privat SNMP-agent om begäran är en UPPSÄTTNINGs typ.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **is_get_type** Pekare för att begära typ status:  
NX_TRUE om Hämta typ  
NX_FALSE om typ av uppsättning

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) returnerade typen
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
Ange kontext motor (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger kontext motorn för SNMP-agenten. Den kan bara användas för SNMPv3-bearbetning. Detta ska anropas innan du skapar säkerhets nycklar om programmet använder autentisering och kryptering, eftersom kontext motorns ID används i processen för att skapa nyckeln. Annars tillhandahåller NetX Duo SNMP ett standard Sammanhangs motor-ID överst i *nxd_snmp. c:*

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **context_engine** Pekare till kontextens motor sträng.
- **context_engine_size** Storlek på kontext motor sträng. Observera att det maximala antalet byte i en kontext motor definieras av NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) konfiguration av SNMP-kontexten har slutförts.
- **NX_NOT_ENABLED** (0X14) SNMPv3 är inte aktiverat
- **NX_SNMP_ERROR** (0X100) kontext motor storleks fel.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
Ange kontext namn (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger kontext namnet för SNMP-agenten. Den kan bara användas för SNMPv3-bearbetning. Om den inte anropas, kommer NetX Duo SNMP-agenten att lämna kontext namnet tomt.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **context_name** Pekare till kontextens namn sträng.
- **context_name_size** Storlek på kontext namn sträng. Observera att det maximala antalet byte i ett kontext namn definieras av NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SNMP-kontexten har skapats.
- **NX_SNMP_ERROR** (0x100) fel i kontext namns storlek.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

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
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en SNMP-agent på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **snmp_agent_name** Pekare till namn strängen för SNMP-agenten.
- **ip_ptr** Pekare till IP-instans.
- **stack_ptr** Pekare till tråd pekare för tråd till SNMP-agent.
- **stack_size** Stack storlek i byte.
- **pool_ptr** Visar standard paketets pool för den här SNMP-agenten.
- **snmp_agent_username_process** Funktions pekare till programmets hanterings rutin för användar namn.
- **snmp_agent_get_process** Funktions pekare till programmets GET reservering-rutin för hantering av förfrågningar.
- **snmp_agent_getnext_process** Funktions pekare till programmets hanterings rutin för GETNEXT-begäran.
- **snmp_agent_set_process** Funktions pekare till program hanterings rutinen ange begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SNMP-agenten har skapats.
- **NX_SNMP_ERROR** (0X100) SNMP-agenten skapa fel.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

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
Hämta SNMP-paketets version

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den SNMP-version som parsas från det senaste SNMP-paketet som togs emot.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **version** Pekare till den SNMP-version som har parsats från mottaget SNMP-paket

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-version Hämta
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Verifiera att den privata strängen matchar agentens privata sträng

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Beskrivning

Den här tjänsten jämför den null-avslutade inaktuella grupp strängen med den privata strängen för SNMP-agenten och anger om de matchar.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **community_string** Pekare till sträng som ska jämföras
- **is_private** Pekare till resultatet av jämförelsen  
NX_TRUE-sträng matchningar  
NX_FALSE strängen matchar inte

### <a name="return-values"></a>Retur värden

- Jämförelse av **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Verifiera att den mottagna offentliga strängen matchar agentens offentliga sträng

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Beskrivning

Den här tjänsten jämför en null-avslutad inmatad grupp sträng med den offentliga SNMP-agentens offentliga sträng och anger om de matchar.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **community_string** Pekare till sträng som ska jämföras
- **is_public** Pekare till resultatet av jämförelsen  
NX_TRUE-sträng matchningar  
NX_FALSE strängen matchar inte

### <a name="return-values"></a>Retur värden

- Jämförelse av **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Ange SNMP-agentens status för varje SNMP-version

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger status (aktive rad/inaktive rad) för var och en av SNMP-versionerna, v1, v2 och v3 på SNMP-agenten. Observera att de användar konfigurerbara alternativen, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 och NX_SNMP_DISABLE_V3 åsidosätter dessa körnings tids inställningar. Som standard är SNMP-agenten aktive rad för alla tre versionerna.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **enabled_v1** Anger aktive rad status för SNMP v1 till på/av.
- **enabled_v2** Aktiverar/inaktiverar aktiverade status för SNMP v2.
- **enabled_v3** Aktiverar/inaktiverar aktiverade status för SNMP v3.

### <a name="return-values"></a>Retur värden

- En lyckad SNMP-version har angetts för **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Ange privat sträng för SNMP-agenten

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger SNMP-agentens privata grupp sträng med den angivna null-indatamängden. Standardvärdet är NULL (ingen privat sträng uppsättning), så att alla SNMP-paket som tas emot med en "privat" grupp sträng inte godkänns av SNMP-agenten för Läs-/skriv åtkomst. Indatasträngen måste vara mindre än eller lika med användaren som kan konfigureras NX_SNMP_MAX_USER_NAME-1 (för att tillåta utrymme för null-avslutning).

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **community_string** Pekare till den privata strängen som ska tilldelas

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett en privat sträng
- **NX_SNMP_ERROR_TOOBIG** (0X01) sträng storleken är för stor 
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten anger SNMP-agentens offentliga community-sträng med null-inmatad sträng. Grupp strängen måste vara mindre än eller lika med användaren som kan konfigureras NX_SNMP_MAX_USER_NAME-1 (för att tillåta utrymme för null-avslutning).

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **community_string** Pekare till den offentliga strängen som ska tilldelas

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett en offentlig sträng
- **NX_SNMP_ERROR_TOOBIG** (0X01) sträng storleken är för stor
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad SNMP-agent.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SNMP-agenten har tagits bort.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
Ange Nätverks gränssnittet för SNMP-agenten

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger SNMP-nätverks gränssnittet för SNMP-agenten som anges av indexet för gränssnittet. Detta är endast användbart för SNMP-värdprogram med NetX Duo 5,6 eller högre som stöder flera nätverks gränssnitt. Standardvärdet om inget värde anges av värden är noll för det primära gränssnittet.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **If_index** Index som anger SNMP-gränssnittet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SNMP-gränssnittet har angetts.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
Skapa en MD5-nyckel (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en MD5-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten är föråldrad. Utvecklare uppmanas att migrera till *nx_snmp_agent_md5_key_create_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **lösen ord** Pekare till lösen ords sträng.
- **destination_key** Pekare till data struktur för SNMP-nyckel.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) nyckeln har skapats.
- Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
Skapa en MD5-nyckel (endast SNMP v3)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en MD5-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten ersätter *nx_snmp_agent_md5_key_create ().* Den här versionen kräver att anroparen anger lösen ords längd.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **lösen ord** Pekare till lösen ords sträng.
- **password_length** Längd på lösen ords sträng.
- **destination_key** Pekare till data struktur för SNMP-nyckel.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) nyckeln har skapats.
- Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.
- **NX_SNMP_FAILED** (0X102) SNMP misslyckades.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
Ange krypterings nyckel för trap-meddelanden

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger att en tidigare skapad sekretess nyckel ska användas för kryptering och dekryptering av SNMPv3-trap-meddelanden.

> [!NOTE]
> *En authentictation-nyckel måste skapas tidigare. SNMP v3-sekretess (kryptering) kräver autentisering. Se nx_snmp_agent_auth_trap_key_use för mer information.*

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **nyckel** Pekare till tidigare skapa nyckel.

### <a name="return-values"></a>Retur värden

- Sekretess nyckeln för **NX_SUCCESS** (0x00) har angetts.
- Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
Ange krypterings nyckel för svarsmeddelanden

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger att den tidigare skapade nyckeln ska användas för kryptering och dekryptering av SNMPv3-svarsmeddelanden.

> [!NOTE]
> *En autentiseringsnyckel måste anges tidigare. SNMP v3-kryptering kräver också att en autentiseringsnyckel skapas. Se nx_snmp_agent_authentiation_key_use för mer information.*

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **nyckel** Pekare till tidigare skapa nyckel.

### <a name="return-values"></a>Retur värden

- Sekretess nyckeln för **NX_SUCCESS** (0x00) har angetts.
- Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

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
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en SHA-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten är föråldrad. Utvecklare uppmanas att migrera till *nx_snmp_agent_sha_key_create_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **lösen ord** Pekare till lösen ords sträng.
- **destination_key** Pekare till data struktur för SNMP-nyckel.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) nyckeln har skapats.
- Fel vid skapande av **NX_SNMP_ERROR** (0X100) nyckel.
- **NX_PTR_ERROR** (0X07) ogiltig SNMP-agent eller nyckel pekare.

### <a name="allowed-from"></a>Tillåten från

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
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en SHA-nyckel som kan användas för autentisering och kryptering.

Den här tjänsten ersätter *nx_snmp_agent_sha_key_create ().* Den här versionen kräver att anroparen anger lösen ords längd.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **lösen ord** Pekare till lösen ords sträng.
- **password_length** Längd på lösen ords sträng.
- **destination_key** Pekare till data struktur för SNMP-nyckel.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) nyckeln har skapats.
- Fel vid skapande av **NX_SNMP_ERROR** (0X100) nyckel.
- Det gick inte att skapa nyckeln **NX_SNMP_FAILED** (0x102).
- **NX_PTR_ERROR** (0X07) ogiltig SNMP-agent eller nyckel pekare.

### <a name="allowed-from"></a>Tillåten från

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
### <a name="description"></a>Beskrivning

Den här tjänsten binder UDP-socketen till SNMP-porten 161 och startar uppgiften SNMP agent Thread.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad start av SNMP-agenten.
- **NX_SNMP_ERROR** (0X100) SNMP agent start fel.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

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
### <a name="description"></a>Beskrivning

Den här tjänsten stoppar SNMP-agentens tråd uppgift och avbinder UDP-socketen till SNMP-porten.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) stoppade SNMP-agenten.
- **NX_PTR_ERROR** (0X07) ogiltig SNMP-agent pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
Skicka SNMPv1 *-trap (endast IPv4)*

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMP-trap till SNMP-hanteraren på den angivna IPv4-adressen. Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att använda tjänsten *nxd_snmp_agent_trap_send* . *nx_snmp_agent_trap_send* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IPv4-adress för SNMP-hanteraren.
- **Enterprise** ID-sträng för företags objekt (sysObectID).
- **trap_type** Typ av trap som begärs, enligt följande:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** Angiven trap-kod.
- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_NOT_ENABLED** (0X14) SNMPv1 är inte aktiverat.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv1 *-trap (IPv4 och IPv6)*

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMP-trap till SNMP-hanteraren på den angivna IP-adressen. Den likvärdiga metoden för att skicka en SNMP-trap i NetX är *nxd_snmp_agent_trap_send* -tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** SNMP-hanterarens IPv4-eller IPv6-adress.
- **Enterprise** ID-sträng för företags objekt (sysObectID).
- **trap_type** Typ av trap som begärs, enligt följande:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** Angiven trap-kod.
- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_NOT_ENABLED** (0X14) SNMPv1 är inte aktiverat.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv2-Trap (endast IPv4)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMPv2-trap till SNMP-hanteraren på den angivna IPv4-adressen. Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv2_send* . *nx_snmp_agent_trapv2_send* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IPv4-adress för SNMP-hanteraren.
- **Community** Grupp namn (användar namn).
- **trap_type**  
   Typ av trap som begärdes. Standard händelserna är:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   För patentskyddade data:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)
   
- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_NOT_ENABLED** (0X14) SNMPv2 är inte aktiverat.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv2-trap genom att ange OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMPv2-trap till SNMP-hanteraren på den angivna IP-adressen (endast IPv4) och tillåter att anroparen anger OID direkt. Den bästa metoden för att skicka en SNMP-trap med angivet OID i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv2_oid_send* . *nx_snmp_agent_trapv2_oid_ skicka* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IP-adress för SNMP-hanteraren.
- **Community** Grupp namn (användar namn).
- **OID** Pekare till buffert som innehåller OID.
- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.
- **NX_OPTION_ERROR** (0X0a) ogiltig parameter.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv2-Trap (IPv4 och IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMP v2-trap till SNMP-hanteraren på den angivna IP-adressen.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IP-adress (IPv4 eller IPv6) för SNMP-hanteraren.
- **Community** Grupp namn (användar namn).
- **trap_type**  
   Typ av trap som begärdes. Standard händelserna är:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   För patentskyddade data:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)

- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_NOT_ENABLED** (0X14) SNMPv2 är inte aktiverat.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) en IP-version som inte stöds
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv2-trap genom att ange OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMP v2-trap till SNMP-hanteraren på den angivna IP-adressen (IPv4/IPv6) och tillåter att anroparen anger OID direkt.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IP-adress för SNMP-hanteraren (IPv4/IPv6).
- **Community** Grupp namn (användar namn).
- **OID** Pekare till buffert som innehåller OID.
- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.
- **NX_OPTION_ERROR** (0X0a) ogiltig parameter.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv3-Trap (endast IPv4)

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMPv3-trap till SNMP-hanteraren på den angivna IPv4-adressen. Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv3_send* . *nx_snmp_agent_trapv3_send* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IPv4-adress för SNMP-hanteraren.
- **användar namn** Grupp namn (användar namn).
- **trap_type**  
   Typ av trap som begärdes. Standard händelserna är:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   För patentskyddade data:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)

- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_NOT_ENABLED** (0X14) SNMPv3 är inte aktiverat.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

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
Skicka SNMPv3-trap genom att ange OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMPv3-trap till SNMP-hanteraren på den angivna IP-adressen (endast IPv4) och tillåter att anroparen anger OID direkt. Den bästa metoden för att skicka en SNMP-trap med angivet OID i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv3_oid_send* . *nx_snmp_agent_trapv3_oid_ skicka* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IP-adress för SNMP-hanteraren.
- **användar namn** Grupp namn (användar namn).
- **OID** Pekare till buffert som innehåller OID.
- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.
- **NX_OPTION_ERROR** (0X0a) ogiltig parameter.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv3-Trap (IPv4 och IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMP-trap till SNMP-hanteraren på den angivna IP-adressen. Denna trap är i princip samma som SNMP v2-Trap, förutom att trap-meddelande formatet finns i SNMP v3 PDU.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** IP-adress (IPv4 eller IPv6) för SNMP-hanteraren.
- **användar namn** Grupp namn (användar namn).
- **trap_type**  
   Typ av trap som begärdes. Standard händelserna är:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   För patentskyddade data:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)

- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_NOT_ENABLED** (0X14) SNMPv3 är inte aktiverat.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) en IP-version som inte stöds
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
Skicka SNMPv3-trap genom att ange OID direkt 

### <a name="prototype"></a>Prototyp

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en SNMPv3-trap till SNMP-hanteraren på den angivna IP-adressen (IPv4/IPv6) och tillåter att anroparen anger OID direkt.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent.
- **ip_address** Pekare till IP-adressen för SNMP-hanteraren.
- **användar namn** Användar namn (community-namn).
- **OID** Pekare till buffert som innehåller OID.
- **elapsed_time** Tids systemet har inträffat (sysUpTime).
- **object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap. Listan har NX_NULL avslut ATS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.
- **NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.
- **NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.
- **NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten anger antalet omstarter som registrerats av SNMP-agenten. Den här tjänsten är bara tillgänglig om SNMPv3 har Aktiver ATS för SNMP-agenten eftersom start antal endast används i SNMPv3-protokollet.

### <a name="input-parameters"></a>Indataparametrar

- **agent_ptr** Pekare till kontroll block för SNMP-agent
- **startar** Värdet för att ange start antal för SNMP-agenten till

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett start antal
- **NX_SNMP_ERROR** (0X100) fel vid inställning av start antal
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

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
Jämför två objekt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Beskrivning

Den här tjänsten jämför det tillhandahållna objekt-ID: t med referens objektets ID. Båda objekt-ID: n är i ASCII SMI-notation, t. ex. att båda objekten måste börja med ASCII-strängen "1.3.6".

Den här tjänsten är föråldrad. Utvecklare uppmanas att migrera till *nx_snmp_object_compare_extended ().*

### <a name="input-parameters"></a>Indataparametrar

- **objekt** Pekare till objekt-ID.
- **reference_object** Pekar mot referens objektets ID.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) objektet matchar referens-objektet.
- **NX_SNMP_NEXT_ENTRY** (0x101) objektet är mindre än referens-objektet.
- **NX_SNMP_ERROR** (0x100) objektet är större än referens-objektet.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

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
Jämför två objekt 

### <a name="prototype"></a>Prototyp

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Beskrivning

Den här tjänsten jämför det tillhandahållna objekt-ID: t med referens objektets ID. Båda objekt-ID: n är i ASCII SMI-notation, t. ex. att båda objekten måste börja med ASCII-strängen "1.3.6".

Den här tjänsten ersätter *nx_snmp_object_compare ().* Den här versionen kräver att anropare anger längd information.

### <a name="input-parameters"></a>Indataparametrar

- **request_object** Pekare för att begära objekt-ID.
- **request_object_length** Längd på objekt-ID för begäran.
- **reference_object** Pekar mot referens objektets ID.
- **reference_object_length** Längden på referens objektets ID.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) objektet matchar referens-objektet.
- **NX_SNMP_NEXT_ENTRY** (0x101) objektet är mindre än referens-objektet.
- **NX_SNMP_ERROR** (0x100) objektet är större än referens-objektet.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

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
### <a name="description"></a>Beskrivning

Den här tjänsten kopierar källobjektet i ASCII SIM-format till målobjektet.

Den här tjänsten är föråldrad. Utvecklare uppmanas att migrera till *nx_snmp_object_copy_extended ().*

### <a name="input-parameters"></a>Indataparametrar

- **source_object_name** Pekare till käll objekt-ID.
- **destination_object_name** Pekare till mål objekt-ID.

### <a name="return-values"></a>Retur värden

- **storlek** Antal byte som kopierats till mål namnet. Om ett fel returneras returneras noll.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten kopierar källobjektet i ASCII SIM-format till målobjektet.

Den här tjänsten ersätter *nx_snmp_object_copy ().* Den här versionen kräver att anropare anger längd information.

### <a name="input-parameters"></a>Indataparametrar

- **source_object_name** Pekare till käll objekt-ID.
- **source_object_name_length** Längd på käll objekt-ID.
- **destination_object_name_buffer** Pekare till mål objektets buffert.
- **destination_object_name_buffer_size** Storlek på mål objektets buffert.

### <a name="return-values"></a>Retur värden

- **storlek** Antal byte som kopierats till mål namnet. Om ett fel returneras returneras noll.

### <a name="allowed-from"></a>Tillåten från

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
Hämta räknar objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar Counter-objektet på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till räknar källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) som Counter-objektet har hämtats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
Ange Counter-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger räknaren på den adress som anges av mål pekaren med räknarvärdet i NetX objekt data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till Counter-mål.
- **object_data** Pekare till käll objekt struktur för räknare.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) Counter-objektet har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

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
Hämta 64-bitars räknar objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar objektet 64-bit Counter på den adress som anges av käll pekaren och placerar den i NetX objekt data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till räknar källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) som Counter-objektet har hämtats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

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
Ange 64-bit Counter-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ställer in 64-bitars räknaren på den adress som anges av mål pekaren med räknarvärdet i objekt data strukturen NetX. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till Counter-mål.
- **object_data** Pekare till käll objekt struktur för räknare.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) Counter-objektet har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
Ange värdet för slut punkt för MIB 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar ett objekt som signalerar slutet av MIB och som vanligt vis anropas från rutinen hämta eller GETNEXT program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **not_used_ptr** Visaren har inte använts – bör vara NX_NULL.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) objekt End-of-MIB-objektet har skapats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
Hämta mätar objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar mätar objektet på den adress som anges av käll pekaren och placerar den i NetX objekt data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till mätar källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) Det gick inte att hämta mätar objektet.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
Ange mätar objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in mätaren på den adress som anges av destinations pekaren med mätar värdet i NetX objekt data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekar mot mätar mål.
- **object_data** Pekare för att mäta käll objekt strukturen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) som mätar objektet har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar objekt-ID (i ASCII SIM-format) på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till objekt-ID-källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) objekt-ID: t har hämtats.
- **NX_SNMP_ERROR** (0X100) ogiltig längd på objekt
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten anger objekt-ID (i ASCII SIM-format) på den adress som anges av mål pekaren med objekt-ID: t i NetX objekt data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekar mot objekt-ID-mål.
- **object_data** Pekare till objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) objekt-ID: t har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
Hämta heltals objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar Integer-objektet på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till heltals källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) som heltals objekt har hämtats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
Ange heltals objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in heltalet på den adress som anges av mål pekaren med heltal svärdet i NetX-objektets data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekar mot heltals mål.
- **object_data** Pekare till objekt strukturen med en heltals källa.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) heltals objekt har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
Hämta IP-adress-objekt (endast IPv4)

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar objektet IP-adress på den adress som anges av käll pekaren och placerar det i NetX objekt data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till IPv4-adress källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IP-objektet har hämtats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
Hämta IP-adress-objekt (endast IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar IPv6-adressprefixet på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur.
Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till IPv6-adress källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IP-objektet har hämtats.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) felaktig kod för inmatad SNMP-objekt
- **NX_NOT_ENABLED** (0X14) IPv6 är inte aktiverat
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
Ange IPv4-adress objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IPv4-adressen på den adress som anges av mål pekaren med IP-adressen i NetX objekt data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till IP-adress att ange.
- **object_data** Pekare till objekt strukturen IP-adress.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IP-adressprefixet har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
Ange IPv6-adress objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IPv6-adressen på den adress som anges av mål pekaren med IP-adressen i NetX objekt data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till IP-adress att ange.
- **object_data** Pekare till objekt strukturen IP-adress.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IPv6-adressen har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_NOT_ENABLED** (0X14) IPv6 är inte aktiverat
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
Ange inget instans objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar ett objekt som signalerar att det inte fanns någon instans av det angivna objektet och som vanligt vis anropas från rutinen hämta eller GETNEXT program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **not_used_ptr** Visaren har inte använts – bör vara NX_NULL.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) objektet nr-instance har skapats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
Det gick inte att hitta objektet 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar ett objekt som signalerar att objektet inte hittades och att det vanligt vis anropas från rutinen hämta eller GETNEXT program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **not_used_ptr** Visaren har inte använts – bör vara NX_NULL.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) objektet som inte hittades har skapats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
Hämta oktett-String-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar oktett-strängen på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till oktett-sträng källa.
- **object_data** Pekare till målets objekt struktur.
- **längd** Antal byte i oktett-sträng.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) strängen för oktett-objektet har hämtats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
Ange oktett-String-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger oktett-strängen på den adress som anges av mål pekaren med oktett-strängen i NetX-objektets data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till oktett-sträng mål.
- **object_data** Pekare till oktettens objekt struktur för sträng källa.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) strängen för oktett-objektet har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
Hämta ASCII-String-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar ASCII-strängen på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekar till ASCII-sträng källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) ASCII-String-objektet har hämtats.
- **NX_SNMP_ERRORs** strängen (0x100) är för stor  
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
Ange ASCII-String-objekt 

### <a name="prototype"></a>Prototyp

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger ASCII-strängen på den adress som anges av mål pekaren med ASCII-strängen i NetX objekt data struktur. Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekar mot ASCII-sträng mål.
- **object_data** Pekar till käll objekts struktur för ASCII-sträng.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) ASCII-String-objektet har kon figurer ATS.
- **NX_SNMP_ERRORs** strängen (0x100) är för stor.
- **NX_SNMP_ERROR_BADVALUE** (0X03) ogiltigt tecken i strängen
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

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

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar timetics på den adress som anges av käll pekaren och placerar den i data strukturen NetX Object. Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.

### <a name="input-parameters"></a>Indataparametrar

- **source_ptr** Pekare till timetics-källa.
- **object_data** Pekare till målets objekt struktur.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) timetics-objektet har hämtats.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

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

### <a name="description"></a>Beskrivning

Den här tjänsten anger timetics-variabeln på den adress som anges av mål pekaren med timetics i objekt data strukturen NetX.
Den här rutinen kallas vanligt vis för att ange program återanrop.

### <a name="input-parameters"></a>Indataparametrar

- **destination_ptr** Pekare till timetics-destination.
- **object_data** Pekare till käll objekts strukturen timetics.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) timetics-objektet har kon figurer ATS.
- **NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.
- **NX_PTR_ERROR** (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```