---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP server Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-tjänster för DHCP-server.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826784"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP server Services

Det här kapitlet innehåller en beskrivning av alla NetX DHCP Server-tjänster.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_dhcp_server_create**: *skapa en DHCP-serverinstans*
- **nx_dhcp_set_interface_network_parameters**: *ange DHCP-Server alternativ för kritiska nätverks parametrar för det angivna gränssnittet*
- **nx_dhcp_create_server_ip_address_list**: *skapa en pool med tillgängliga IP-adresser som ska tilldelas till DHCP-klienter*
- **nx_dhcp_clear_client_record**: *ta bort klient posten i Server databasen*
- **nx_dhcp_server_delete**: *ta bort en DHCP-instans*
- **nx_dhcp_server_start**: *starta eller återuppta DHCP-server bearbetning*
- **nx_dhcp_server_stop**: *stoppa DHCP-server bearbetning*

## <a name="nx_dhcp_server_create"></a>nx_dhcp_server_create

Skapa en DHCP-serverinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en DHCP-serverinstans med en tidigare skapad IP-instans.

> [!IMPORTANT]
> Programmet måste se till att den modempool som skapas för tjänsten för IP-skapande har en minimum548 byte-nyttolast, inte inklusive UDP-, IP-och Ethernet-huvudena.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr**: pekar mot kontroll block för DHCP-server.  
- **ip_ptr**: pekar mot IP-instans för DHCP-server.
- **stack_ptr**: pekare DHCP-serverns stack plats.
- **stack_size**: storleken på DHCP-serverns stack
- **input_address_list**: pekar på server lista över IP-adresser
- **name_ptr**: pekare till DHCP-servernamnet
- **packet_pool_ptr**: pekare till DHCP-serverns pakets bassäng

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) DHCP-servern har skapats.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0XA9) paket nytto last för litet fel
- **NX_DHCP_NO_SERVER_OPTION_LIST**: (0X96) Server alternativ listan är tom
- NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.
- NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en networkinterface specifik pool med tillgängliga IP-adresser för den angivna DHCP-servern som ska tilldelas. Start-och slut-IP-adresserna måste matcha det angivna nätverks gränssnittet. Det faktiska antalet IP-adresser som lagts till kan vara mindre än det totala antalet adresser om IP-adress listan inte är tillräckligt stor (vilket anges i den användar konfigurerbara *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parametern).

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-serverns kontroll block.  
- **iface_index**: index som motsvarar nätverks gränssnittet
- **start_ip_address**: första tillgängliga IP-adress
- **end_ip_address**: sista tillgängliga IP-adress
- **addresses_added**: antal IP-adresser som lagts till i listan

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) DHCP-servern har skapats.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0XA1) indexet matchar inte adresser
- **NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0X99) ogiltig adress indata
- NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start-/slut adresser
- NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.

### <a name="allowed-from"></a>Tillåten från

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

Ta bort klient posten från Server databasen

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar klient posten från Server databasen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr**: pekar mot kontroll block för DHCP-server.  
- **dhcp_client_ptr**: pekare till DHCP-klienten som ska tas bort

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) DHCP-servern har skapats.
- NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.
- NX_CALLER_ERROR: (0x11) icke-tråd som anropar tjänsten

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Ange Nätverks parametrar för DHCP-alternativ

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in standardvärden för nätverks kritiska parametrar för det angivna gränssnittet. DHCP-servern kommer att inkludera de här alternativen i erbjudandet och bekräftelse svar på DHCP-klienten. Om värd uppsättningens gränssnitts parametrar som en DHCP-server körs på, kommer parametrarna att försättas enligt följande: routern är inställd på den primära gatewayen för DHCP-servern, DNS-serveradressen till själva DHCP-servern och nät masken till samma som DHCP-serverns gränssnitt har kon figurer ATS med.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr**: pekar mot kontroll block för DHCP-server.  
- **iface_index**: index som motsvarar nätverks gränssnittet
- **subnet_mask**: nät mask för klient nätverk
- **default_gateway_address**: klientens IP-adress för router
- **dns_server_address**: DNS-server för klient nätverk

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) DHCP-servern har skapats.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0XA1) indexet matchar inte adresser
- **NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0XA3) ogiltiga nätverks parametrar
- NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad DHCP-serverinstans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr**: pekar mot en DHCP-serverinstans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) DHCP-servern har tagits bort.
- NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.
- NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Starta bearbetning av DHCP-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar DHCP-server bearbetning, vilket innefattar att skapa en server UDP-socket, binda DHCP-porten och vänta på att ta emot klient-DHCP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad Server start.  
- **NX_DHCP_ALREADY_STARTED**: (0X93) DHCP har redan startats.
- NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.
- NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a>Se även

nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Stoppar DHCP-server bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar DHCP-serverns bearbetning, vilket innefattar att ta emot begär Anden om DHCP-klienter.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr**: pekar mot DHCP-serverinstansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) DHCP-stopp har slutförts.
- **NX_DHCP_ALREADY_STARTED**: (0X93) DHCP har redan startats.
- NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.
- NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
