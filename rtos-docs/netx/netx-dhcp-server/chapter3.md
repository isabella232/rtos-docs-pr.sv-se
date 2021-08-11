---
title: Kapitel 3 – Beskrivning av Azure RTOS NetX DHCP-servertjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX DHCP-servertjänster.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 702499184b12484fa5862ba83ff3fadb8fccea31089b6bf8b71daf267e8c84a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799531"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX DHCP-servertjänster

Det här kapitlet innehåller en beskrivning av alla NetX DHCP-servertjänster.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

- **nx_dhcp_server_create:** Skapa *en DHCP-serverinstans*
- **nx_dhcp_set_interface_network_parameters: Ange** *DHCP-serveralternativ för kritiska nätverksparametrar för angivet gränssnitt*
- **nx_dhcp_create_server_ip_address_list: Skapa** *en pool med tillgängliga IP-adresser som ska tilldelas till GRÄNSSNITTET DHCP-klienter*
- **nx_dhcp_clear_client_record:** Ta *bort klientposten i serverdatabasen*
- **nx_dhcp_server_delete:** Ta *bort en DHCPServer-instans*
- **nx_dhcp_server_start:** *Starta eller återuppta bearbetning av DHCP-server*
- **nx_dhcp_server_stop:** Stoppa *DHCP-serverbearbetning*

## <a name="nx_dhcp_server_create"></a>nx_dhcp_server_create

Skapa en DHCP-serverinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skapar en DHCP-serverinstans med en tidigare skapad IP-instans.

> [!IMPORTANT]
> Programmet måste se till att paketpoolen som skapades för IP-tjänsten för att skapa har en minsta 548 byte-nyttolast, inte UDP-, IP- och Ethernet-huvudena.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr:** Pekare till DHCP-serverkontrollblock.  
- **ip_ptr: Pekare** till DHCP-serverns IP-instans.
- **stack_ptr: Pekare** för DHCP-serverstackplats.
- **stack_size:** Storleken på DHCP-serverstacken
- **input_address_list:** Pekare till serverns lista över IP-adresser
- **name_ptr**: Pekare till DHCP-servernamn
- **packet_pool_ptr: Pekare** till DHCP-serverpaketpool

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DHCP-server skapas.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Paketnyttolasten är för liten
- **NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Listan över serveralternativ är tom
- NX_DHCP_PARAMETER_ERROR: (0x92) Ogiltiga indata som inte pekare
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.
- NX_PTR_ERROR: (0x16) Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

Skapa en IP-adresspool

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Description

Den här tjänsten skapar en nätverksinterface-specifik pool med tillgängliga IP-adresser för den angivna DHCP-server som ska tilldelas. Start- och slut-IP-adresserna måste matcha det angivna nätverksgränssnittet. Det faktiska antalet IP-adresser som läggs till kan vara mindre än det totala antalet adresser om IP-adresslistan inte är tillräckligt stor (vilket anges i den användarkonfigurerbara *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till KONTROLLblock för DHCP-server.  
- **iface_index:** Index som motsvarar nätverksgränssnittet
- **start_ip_address:** Första tillgängliga IP-adress
- **end_ip_address:** Sista tillgängliga IP-adressen
- **addresses_added:** Antal IP-adresser som lagts till i listan

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DHCP-server skapas.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index matchar inte adresser
- **NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Ogiltig adressinmatning
- NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Ologisk start-/slutadresser
- NX_PTR_ERROR: (0x16) Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

Ta bort klientposten från serverdatabasen

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar klientposten från serverdatabasen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr:** Pekare till DHCP-serverkontrollblock.  
- **dhcp_client_ptr: Pekare** till DHCP-klienten som ska tas bort

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DHCP-server skapas.
- NX_PTR_ERROR: (0x16) Ogiltig pekare.
- NX_CALLER_ERROR: (0x11) Icke-trådanropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Ange nätverksparametrar för DHCP-alternativ

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a>Description

Den här tjänsten anger standardvärden för nätverkskritiska parametrar för det angivna gränssnittet. DHCP-servern inkluderar dessa alternativ i erbjudandet och ACK svarar på DHCP-klienten. Om gränssnittsparametrarna för värduppsättningen som en DHCP-server körs på anges standardparametrarna på följande sätt: routern är inställd på den primära gränssnittsgatewayen för själva DHCP-servern, DNS-serveradressen till själva DHCP-servern och nätmasken till samma som DHCP-servergränssnittet konfigureras med.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr:** Pekare till DHCP-serverkontrollblock.  
- **iface_index:** Index som motsvarar nätverksgränssnittet
- **subnet_mask:** Nätmask för klientnätverk
- **default_gateway_address:** Klientens router-IP-adress
- **dns_server_address:** DNS-server för klientens nätverk

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DHCP-server skapas.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index matchar inte adresser
- **NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Ogiltiga nätverksparametrar
- NX_PTR_ERROR: (0x16) Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

Ta bort en DHCP-serverinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad DHCP-serverinstans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr: Pekare** till en DHCP-serverinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad BORTTAGNING av DHCP-server.
- NX_PTR_ERROR: (0x16) Ogiltig pekare.
- NX_DHCP_PARAMETER_ERROR: (0x92) Ogiltig icke-pekarindata
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Starta DHCP-serverbearbetning

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar DHCP-serverbearbetning, vilket innefattar att skapa en UDP-serversocket, binda DHCP-porten och vänta på att ta emot DHCP-klientbegäranden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr:** Pekare till en DHCP-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad serverstart.  
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP har redan startats.
- NX_PTR_ERROR: (0x16) Ogiltig pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.
- NX_DHCP_PARAMETER_ERROR: (0x92) Ogiltig icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a>Se även

nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Stoppar DHCP-serverbearbetning

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar DHCP-serverbearbetning, vilket innefattar att ta emot DHCP-klientbegäranden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr: Pekare** till DHCP-serverinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Dhcp-stopp.
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP har redan startats.
- NX_PTR_ERROR: (0x16) Ogiltig pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.
- NX_DHCP_PARAMETER_ERROR: (0x92) Ogiltig icke-pekarindata.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
