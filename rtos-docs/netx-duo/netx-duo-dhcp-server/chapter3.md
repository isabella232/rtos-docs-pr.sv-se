---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DHCP server Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCP Server-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826106"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DHCP server Services

Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCP Server-tjänster (visas nedan) i alfabetisk ordning.

> [!NOTE]
> I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

## <a name="nx_dhcp_server-create"></a>nx_dhcp_server skapa

Skapa en DHCP-serverinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en DHCP-serverinstans med en tidigare skapad IP-instans.

> [!IMPORTANT]
> Programmet måste se till att Packet-poolen som skapas för tjänsten för IP-skapande har en minimal 548 byte-nyttolast, inte inklusive UDP-, IP-och Ethernet-huvudena.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-serverns kontroll block.
- **ip_ptr** Pekare till DHCP-serverns IP-instans.
- **stack_ptr** Pekare för DHCP-serverns stack plats.
- **Stack_size storleken på DHCP-serverns stack** input_address_list pekare till server lista över IP-adresser
- **Name_ptr pekare till DHCP-serverns namn** packet_pool_ptr pekare till DHCP-serverns paket-pool

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-servern har skapats.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0XA9) paket nytto last för litet fel
- **NX_DHCP_NO_SERVER_OPTION_LIST** (0X96) Server alternativ listan är tom
- NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.
- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

Skapa en IP-adresspool

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en specifik pool med tillgängliga IP-adresser för den angivna DHCP-servern som ska tilldelas. Start-och slut-IP-adresserna måste matcha det angivna nätverks gränssnittet. Det faktiska antalet IP-adresser som lagts till kan vara mindre än det totala antalet adresser om IP-adress listan inte är tillräckligt stor (vilket anges i den användar konfigurerbara *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parametern).

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-serverns kontroll block.
- **iface_index** Index som motsvarar nätverks gränssnittet
- **start_ip_address** Första tillgängliga IP-adress
- **end_ip_address** Sista tillgängliga IP-adress
- **addresses_added** Antal IP-adresser som lagts till i listan

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-servern har skapats.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0XA1) indexet matchar inte adresser
- **NX_DHCP_INVALID_IP_ADDRESS_LIST** (0X99) ogiltig adress indata
- NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start-/slut adresser
- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

Ta bort klient posten från Server databasen

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar klient posten från Server databasen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-serverns kontroll block.
- **dhcp_client_ptr pekare till DHCP-klienten som ska tas bort**

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-servern har skapats.
- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.
- NX_CALLER_ERROR (0x11) icke-tråd som anropar tjänsten

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Ange Nätverks parametrar för DHCP-alternativ

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in standardvärden för nätverks kritiska parametrar för det angivna gränssnittet. DHCP-servern kommer att inkludera de här alternativen i erbjudandet och bekräftelse svar på DHCP-klienten. Om värd uppsättningens gränssnitts parametrar som en DHCP-server körs på, kommer parametrarna att försättas enligt följande: routern är inställd på den primära gatewayen för DHCP-servern, DNS-serveradressen till själva DHCP-servern och nät masken till samma som DHCP-serverns gränssnitt har kon figurer ATS med.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-serverns kontroll block.
- **iface_index** Index som motsvarar nätverks gränssnittet
- **subnet_mask** Nätmask för klient nätverk
- **default_gateway_address** Klientens IP-adress för router
- **dns_server_address** DNS-server för klient nätverk

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-servern har skapats.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0XA1) indexet matchar inte adresser
- **NX_DHCP_INVALID_NETWORK_PARAMETERS** (0XA3) ogiltiga nätverks parametrar
- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

Ta bort en DHCP-serverinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad DHCP-serverinstans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en DHCP-serverinstans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-servern har tagits bort.
- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.
- NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Starta bearbetning av DHCP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar DHCP-server bearbetning, vilket innefattar att skapa en server UDP-socket, binda DHCP-porten och vänta på att ta emot klient-DHCP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) Server start har slutförts.
- **NX_DHCP_ALREADY_STARTED** (0X93) DHCP har redan startats.
- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.
- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.
- NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Stoppar DHCP-server bearbetning

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar DHCP-serverns bearbetning, vilket innefattar att ta emot begär Anden om DHCP-klienter.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-serverinstansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-stopp.
- **NX_DHCP_ALREADY_STARTED** (0X93) DHCP har redan startats.
- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.
- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.
- NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
