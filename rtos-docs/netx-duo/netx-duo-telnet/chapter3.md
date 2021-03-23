---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Telnet-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo Telnet-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825713"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Telnet-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo Telnet-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_telnet_client_connect**: *Anslut en Telnet-klient med IPv4-adress*
- **nxd_telnet_client_connect**: *Anslut en IPv6 Telnet-klient med IPv6-adress*
- **nx_telnet_client_create**: *skapa en Telnet-klient*
- **nx_telnet_client_delete**: *ta bort en Telnet-klient*
- **nx_telnet_client_disconnect**: *Koppla från en Telnet-klient*
- **nx_telnet_client_packet_receive**: *ta emot paket via Telnet-klienten*
- **nx_telnet_client_packet_send**: *skicka paket via Telnet-klienten*
- **nx_telnet_server_create**: *skapa en Telnet-Server*
- **nx_telnet_server_delete**: *ta bort en Telnet-Server*
- **nx_telnet_server_disconnect**: *Koppla från en Telnet-klient*
- **nx_telnet_server_get_open_connection_count**: *Hämta antalet öppna anslutningar*
- **nx_telnet_server_packet_send**: *skicka paket via klient anslutning*
- **nx_telnet_server_packet_pool_set**: *Ange paket bassäng som programpool för Telnet-Server*
- **nx_telnet_server_start**: *starta en Telnet-Server*
- **nx_telnet_server_stop**: *stoppa en Telnet-Server*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

Ansluta en Telnet-klient med IPv4-adress

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker ansluta den tidigare skapade Telnet-klientprogrammet till servern på den angivna IP-adressen och porten med hjälp av en IPv4-adress för Telnet-servern. Den här tjänsten infogar faktiskt ULONG-serverns IP-adress i ett NXD_ADDRESS Control-Block och ställer in IP-versionen på 4 innan du anropar den *nxd_telnet_client_connect* tjänst som beskrivs nedan.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr**: pekar på kontroll block för Telnet-klienten.
- **server_ip**: Telnet-serverns IPv4-adress.
- **SERVER_PORT**: TCP-porten för Server (Telnet Server är port 23).
- **wait_option**: anger hur länge tjänsten ska vänta på anslutning till Telnet-klienten. Vänte alternativen definieras enligt följande:

    - **timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.
    - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad klient anslutning.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4)-klienten är redan ansluten.
- NX_PTR_ERROR: (0x07) ogiltig klient pekare.
- NX_IP_ADDRESS_ERROR: (0x21) ogiltig IP-adress.
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

Ansluta en Telnet-klient med IPv6-eller IPv4-adress

### <a name="prototype"></a>Prototyp

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker ansluta den tidigare skapade Telnet-klientprogrammet till servern på den angivna IP-adressen och porten med hjälp av Telnet-serverns IPv6-adress. Den här tjänsten kan ta en IPv4-eller IPv6-adress men måste finnas i NXD_ADDRESS variabel *server_ip_address.*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr**: pekar på kontroll block för Telnet-klienten.
- **server_ip_address**: serverns IP-adress.
- **SERVER_PORT**: TCP-porten för Server (Telnet Server är port 23).
- **wait_option**: anger hur länge tjänsten ska vänta på anslutning till Telnet-klienten. Vänte alternativen definieras enligt följande:

    - **timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.
    - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad klient anslutning.
- **NX_TELNET_ERROR**: (0XF0) klient anslutnings fel.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4)-klienten är redan ansluten.
- NX_PTR_ERROR: (0x07) ogiltig klient pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.
- NX_TELNET_INVALID_PARAMETER: (0xF5) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a>nx_telnet_client_create

Skapa en Telnet-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en Telnet-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr**: pekar på kontroll block för Telnet-klienten.
- **client_name**: namnet på klient instansen.
- **ip_ptr**: pekare till IP-instans.
- **window_size**: storleken på TCP Receive-fönstret för den här klienten.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad klient skapande.
- **NX_TELNET_ERROR**: (0XF0) socket-skapande fel.
- NX_PTR_ERROR: (0x07) ogiltig klient eller IP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a>nx_telnet_client_delete

Ta bort en Telnet-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad Telnet-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr**: pekar på kontroll block för Telnet-klienten.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad klient borttagning.
- **NX_TELNET_NOT_DISCONNECTED**: (0XF4) klienten är fortfarande ansluten.
- NX_PTR_ERROR: (0x07) ogiltig klient pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a>nx_telnet_client_disconnect

Koppla från en Telnet-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar från en tidigare ansluten Telnet-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr**: pekar på kontroll block för Telnet-klienten.
- **wait_option**: anger hur länge tjänsten ska vänta tills Telnet-klienten kopplas från. Vänte alternativen definieras enligt följande:

    - **timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.
    - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad klient från koppling.
- **NX_TELNET_NOT_CONNECTED**: (0XF3) klienten är inte ansluten.
- NX_PTR_ERROR: (0x07) ogiltig klient pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.


### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

Ta emot paket via Telnet Client

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar emot ett paket från den tidigare anslutna Telnet Client-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr**: pekar på kontroll block för Telnet-klienten.
- **packet_ptr**: pekar mot målet för det mottagna paketet.
- **wait_option**: anger hur länge tjänsten ska vänta på att det tar emot Telnet-klientcertifikatet. Vänte alternativen definieras enligt följande:
    - **timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.
    - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad klient paket mottagning.
- NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

Skicka paket via Telnet Client

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett paket genom den tidigare anslutna Telnet-klientprogrammet.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr**: pekar på kontroll block för Telnet-klienten.
- **packet_ptr**: pekar på det paket som ska skickas.
- **wait_option**: anger hur länge tjänsten ska vänta på att skicka Telnet-klienten. Vänte alternativen definieras enligt följande:
    - **timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.
    - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades skicka klient paket.
- **NX_TELNET_ERROR**: (0xF0) Det gick inte att skicka paket – anroparen ansvarar för att släppa paketet.
- NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

Skapa en Telnet-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en Telnet Server-instans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot kontroll block för Telnet-Server.
- **server_name**: namnet på Telnet Server-instansen.
- **ip_ptr**: pekar mot associerad IP-instans.
- **stack_ptr**: pekare till stack för den interna Server tråden.
- **sack_size**: stackens storlek i byte.
- **new_connection**: funktions pekare för motringning av program. Den här rutinen anropas när en ny anslutnings förfrågan för Telnet-klienten identifieras av servern.
- **receive_data**: funktions pekare för motringning av program. Den här rutinen anropas när det finns nya Telnet-klientinställningar på anslutningen. Den här rutinen ansvarar för att släppa paketet.
- **end_connection**: funktions pekare för motringning av program. Den här rutinen anropas när en anslutning för Telnet-klienten kopplas från av klienten eller om klient anslutnings tiden upphör ("aktivitetens timeout upphör att gälla). Servern kan också koppla från tjänsten *nx_telnet_server_disconnect* som beskrivs nedan.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad Server skapande.
- NX_PTR_ERROR: (0x07) ogiltig pekare för Server, IP, stack eller program.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a>nx_telnet_server_delete

Ta bort en Telnet-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad Telnet Server-instans.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot kontroll block för Telnet-Server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad Server borttagning.
- NX_PTR_ERROR: (0x07) ogiltig Server pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a>nx_telnet_server_disconnect

Koppla från en Telnet-klient

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar från en tidigare ansluten klient på den här Telnet-serverinstansen. Den här rutinen anropas vanligt vis från programmets motringnings funktion för mottagning av data som svar på ett villkor som upptäckts i mottagna data.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot kontroll block för Telnet-Server.
- **logical_connection**: logisk anslutning motsvarande klient anslutningen på den här servern. Giltigt värde intervall från 0 till NX_TELENET_MAX_CLIENTS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad Server från koppling.
- **NX_TELNET_ERROR**: det gick inte att koppla från servern (0xF0).
- NX_OPTION_ERROR: (0x0A) ogiltig logisk anslutning.
- NX_PTR_ERROR: (0x07) ogiltig Server pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

Returnera antalet öppna anslutningar

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar antalet Telnet-klienter som är anslutna till varandra.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot kontroll block för Telnet-Server.
- **Connection_count**: pekar på minne för att lagra antal anslutningar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutfördes.
- NX_PTR_ERROR: (0x07) ogiltig Server pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

Skicka paket via klient anslutning

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett paket till klient anslutningen på den här Telnet-serverinstansen. Den här rutinen anropas vanligt vis från programmets motringnings funktion för mottagning av data som svar på ett villkor som upptäckts i mottagna data.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot kontroll block för Telnet-Server.
- **logical_connection**: logisk anslutning motsvarande klient anslutningen på den här servern. Giltigt värde intervall från 0 till NX_TELENET_MAX_CLIENTS.
- **packet_ptr**: pekar på det mottagna paketet.
- **wait_option**: anger hur länge tjänsten ska vänta på att Telnet Server-paketet ska skickas. Vänte alternativen definieras enligt följande:
    - **timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.
    - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran. 

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutfört paket sändning.
- **NX_TELNET_FAILED**: (0XF2) TCP-socket-sändning misslyckades.
- NX_OPTION_ERROR: (0x0A) ogiltig logisk anslutning.
- NX_PTR_ERROR: (0x07) ogiltig Server pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

Ange tidigare skapade Packet bassäng som Telnet-adresspool

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>Beskrivning

Den här tjänsten anger en tidigare skapad modempool som programpoolen för Telnet-servern om NX_TELNET_SERVER_USER_CREATE_PACKET_POOL har definierats. Det kräver också att NX_TELNET_SERVER_OPTION_DISABLE inte definieras så att Telnet-servern behöver en modempool för att överföra Telnet-alternativ till Telnet-klienter.

Detta gör det möjligt för program att skapa en modempool i olika minnen, t. ex. minne utan cache, än i Telnet-serverns stack. Observera att om den här funktionen inte kontrollerar om programpoolen för Telnet-servern redan har angetts. Om den anropas på en icke-null-pekare för en Telnet-Server, kommer den att skriva över den och ersätta den befintliga poolen med pakethuvuden som intrycks av insamlings pekaren.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekare till kontroll block för Telnet-Server
- **packet_pool_ptr**: pekare till tidigare skapade paketets pool

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) har angett poolen.
- NX_PTR_ERROR: (0x07) ogiltig Server pekare.

### <a name="allowed-from"></a>Tillåten från

Init, trådar

### <a name="example"></a>Exempel

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a>nx_telnet_server_start

Starta en Telnet-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en tidigare skapad Telnet Server-instans.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot kontroll block för Telnet-Server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) har startats.
- **NX_TELNET_NO_PACKET_POOL**: (0XF6) ingen paket uppsättnings uppsättning
- NX_PTR_ERROR: (0x07) ogiltig Server pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Stoppa en Telnet-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar en tidigare skapad och startad Telnet Server-instans.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot kontroll block för Telnet-Server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) har stoppats
- NX_PTR_ERROR: (0x07) ogiltig Server pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare av tjänst

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```