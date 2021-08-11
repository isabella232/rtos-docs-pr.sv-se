---
title: Kapitel 3 – Beskrivning av Azure RTOS NetX Duo Telnet-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo Telnet Services (listas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 70bf4016793572d7327d12be182750316659c3c4260d2f7db8acddbba00c5601
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792000"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX Duo Telnet-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo Telnet Services (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

- **nx_telnet_client_connect**: *Anslut en Telnet-klient med IPv4-adress*
- **nxd_telnet_client_connect:** Anslut *en IPv6 Telnet-klient med IPv6-adress*
- **nx_telnet_client_create:** Skapa *en Telnet-klient*
- **nx_telnet_client_delete:** Ta *bort en Telnet-klient*
- **nx_telnet_client_disconnect:** Koppla *från en Telnet-klient*
- **nx_telnet_client_packet_receive:** Ta *emot paket via Telnet-klienten*
- **nx_telnet_client_packet_send:** *Skicka paket via Telnet-klienten*
- **nx_telnet_server_create:** Skapa *en Telnet-server*
- **nx_telnet_server_delete:** Ta *bort en Telnet-server*
- **nx_telnet_server_disconnect:** Koppla *från en Telnet-klient*
- **nx_telnet_server_get_open_connection_count:** Hämta *antalet öppna anslutningar*
- **nx_telnet_server_packet_send:** Skicka *paket via klientanslutning*
- **nx_telnet_server_packet_pool_set:** Ange *paketpoolen som Telnet Server-paketpool*
- **nx_telnet_server_start:** *Starta en Telnet-server*
- **nx_telnet_server_stop:** *Stoppa en Telnet-server*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

Anslut en Telnet-klient med IPv4-adress

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker ansluta den tidigare skapade Telnet-klientinstansen till servern på den angivna IP-adressen och porten med hjälp av en IPv4-adress för Telnet-servern. Den här tjänsten infogar faktiskt ULONG-serverns IP-adress i ett NXD_ADDRESS-kontrollblock och anger IP-versionen till 4 innan *den anropar nxd_telnet_client_connect tjänsten* som beskrivs nedan.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr:** Pekare till Telnet-klientens kontrollblock.
- **server_ip:** IPv4-adressen för Telnet-servern.
- **server_port:** TCP-serverporten (Telnet-servern är port 23).
- **wait_option:** Definierar hur länge tjänsten ska vänta på telnet-klientens anslutning. Väntealternativen definieras på följande sätt:

    - **timeout-värde:**(0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan Telnet Server-svaret väntar.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad klient-anslutning.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) Klienten är redan ansluten.
- NX_PTR_ERROR: (0x07) Ogiltig klient pekare.
- NX_IP_ADDRESS_ERROR: (0x21) Ogiltig IP-adress.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

Anslut en Telnet-klient med IPv6- eller IPv4-adress

### <a name="prototype"></a>Prototyp

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker ansluta den tidigare skapade Telnet-klientinstansen till servern på den angivna IP-adressen och porten med hjälp av Telnet-serverns IPv6-adress. Den här tjänsten kan ta en IPv4- eller IPv6-adress, men måste finnas i *NXD_ADDRESS-server_ip_address.*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr:** Pekare till Telnet-klientens kontrollblock.
- **server_ip_address:** IP-adress för server.
- **server_port:** TCP-serverporten (Telnet-servern är port 23).
- **wait_option:** Definierar hur länge tjänsten ska vänta på telnet-klientens anslutning. Väntealternativen definieras på följande sätt:

    - **timeout-värde:**(0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan Telnet Server-svaret väntar.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad klient-anslutning.
- **NX_TELNET_ERROR**: (0xF0) Klient connect-fel.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) Klienten är redan ansluten.
- NX_PTR_ERROR: (0x07) Ogiltig klient pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.
- NX_TELNET_INVALID_PARAMETER: (0xF5) Ogiltiga indata som inte pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar en Telnet-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr:** Pekare till Telnet-klientens kontrollblock.
- **client_name:** Namnet på klientinstansen.
- ip_ptr : **Pekare** till IP-instans.
- **window_size:** Storleken på TCP-mottagningsfönstret för den här klienten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckades Klient skapas.
- **NX_TELNET_ERROR:**(0xF0) Socket create-fel.
- NX_PTR_ERROR: (0x07) Ogiltig klient eller IP-pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort en telnet-klientinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr:** Pekare till Telnet-klientens kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Borttagning av klient.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) Klienten är fortfarande ansluten.
- NX_PTR_ERROR: (0x07) Ogiltig klient pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten kopplar från en tidigare ansluten Telnet-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr:** Pekare till Telnet-klientkontrollblocket.
- **wait_option:** Definierar hur länge tjänsten ska vänta på att Telnet-klienten kopplas från. Väntealternativen definieras på följande sätt:

    - **timeout-värde:**(0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på Telnet Server-svaret.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Klienten kopplas från.
- **NX_TELNET_NOT_CONNECTED**: (0xF3) Klienten är inte ansluten.
- NX_PTR_ERROR: (0x07) Ogiltig klientpekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.


### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

Ta emot paket via Telnet-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten tar emot ett paket från den tidigare anslutna Telnet-klientinstansen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr:** Pekare till Telnet-klientkontrollblocket.
- **packet_ptr:** Pekare till målet för det mottagna paketet.
- **wait_option:** Definierar hur länge tjänsten ska vänta på att Telnet-klientpaketet tas emot. Väntealternativen definieras på följande sätt:
    - **timeout-värde:**(0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på Telnet Server-svaret.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad klientpaket tar emot.
- NX_PTR_ERROR: (0x07) Ogiltig pekare
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

Skicka paket via Telnet-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett paket via den tidigare anslutna Telnet-klientinstansen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr:** Pekare till Telnet-klientkontrollblocket.
- **packet_ptr:** Pekare till det paket som ska skickas.
- **wait_option:** Definierar hur länge tjänsten ska vänta på att Telnet-klientpaketet skickas. Väntealternativen definieras på följande sätt:
    - **timeout-värde:**(0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på Telnet Server-svaret.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills Telnet-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad klientpaketssändning.
- **NX_TELNET_ERROR**: (0xF0) Skicka paket misslyckades – anroparen ansvarar för att släppa paketet.
- NX_PTR_ERROR: (0x07) Ogiltig pekare
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

Skapa en Telnet-server

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

### <a name="description"></a>Description

Den här tjänsten skapar en Telnet Server-instans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet Server-kontrollblocket.
- **server_name:** Namnet på Telnet Server-instansen.
- **ip_ptr: Pekare** till associerad IP-instans.
- **stack_ptr:** Pekare till stack för den interna servertråden.
- **sack_size:** Stackens storlek, i byte.
- **new_connection: Funktionspekare** för programanropsrutinen. Den här rutinen anropas när en ny Telnet-klientanslutningsbegäran identifieras av servern.
- **receive_data: Funktionspekare** för programanropsrutinen. Den här rutinen anropas när det finns nya Telnet-klientdata i anslutningen. Den här rutinen ansvarar för att släppa paketet.
- **end_connection: Funktionspekare** för programanropsrutinen. Den här rutinen anropas när en Telnet-klientanslutning kopplas från av klienten eller om klientanslutningen går ut ("tidsgräns för aktivitet" upphör). Servern kan också koppla från via *nx_telnet_server_disconnect* som beskrivs nedan.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Skapa servern.
- NX_PTR_ERROR: (0x07) Ogiltig server, IP- eller stack- eller programanropspekare.

### <a name="allowed-from"></a>Tillåts från

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

Ta bort en Telnet-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en telnet-serverinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet Server-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad server-borttagning.
- NX_PTR_ERROR: (0x07) Ogiltig server-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten kopplar från en tidigare ansluten klient på den här Telnet Server-instansen. Den här rutinen anropas vanligtvis från programmets återanropsfunktion för att ta emot data som svar på ett villkor som identifierats i de data som tas emot.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet Server-kontrollblocket.
- **logical_connection:** Logisk anslutning som motsvarar klientanslutningen på den här servern. Giltigt värdeintervall mellan 0 och NX_TELENET_MAX_CLIENTS.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Servern kopplas från.
- **NX_TELNET_ERROR**: (0xF0) Det gick inte att koppla från servern.
- NX_OPTION_ERROR: (0x0A) Ogiltig logisk anslutning.
- NX_PTR_ERROR: (0x07) Ogiltig server-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

Returnera antalet anslutningar som är öppna för tillfället

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Description

Den här tjänsten returnerar antalet telnet-klienter som för närvarande är anslutna.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet Server-kontrollblocket.
- **Connection_count:** Pekare till minnet för att lagra antalet anslutningar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckades.
- NX_PTR_ERROR: (0x07) Ogiltig server-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

Skicka paket via klientanslutning

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett paket till klientanslutningen på den här Telnet Server-instansen. Den här rutinen anropas vanligtvis från programmets återanropsfunktion för att ta emot data som svar på ett villkor som identifierats i de data som tas emot.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet Server-kontrollblocket.
- **logical_connection:** Logisk anslutning som motsvarar klientanslutningen på den här servern. Giltigt värdeintervall mellan 0 och NX_TELENET_MAX_CLIENTS.
- **packet_ptr:** Pekare till det mottagna paketet.
- **wait_option:** Definierar hur länge tjänsten ska vänta på att Telnet Server-paketet ska skickas. Väntealternativen definieras på följande sätt:
    - **timeout-värde:**(0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på Telnet Server-svaret.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills Telnet-servern svarar på begäran. 

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad paketsändning.
- **NX_TELNET_FAILED**: (0xF2) TCP socket send misslyckades.
- NX_OPTION_ERROR: (0x0A) Ogiltig logisk anslutning.
- NX_PTR_ERROR: (0x07) Ogiltig server-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

Ange en paketpool som skapats tidigare som Telnet-serverpool

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>Description

Den här tjänsten anger en paketpool som skapats tidigare som Telnet Server-paketpool om NX_TELNET_SERVER_USER_CREATE_PACKET_POOL har definierats. Det kräver också att NX_TELNET_SERVER_OPTION_DISABLE definieras så att Telnet-servern behöver en paketpool för att överföra Telnet-alternativ till Telnet-klienter.

Detta gör att program kan skapa paketpoolen i ett annat minne, t.ex. inget cacheminne, än Telnet Server-stacken. Observera att om den här funktionen inte kontrollerar om Telnet Server-paketpoolen redan har angetts. Om den anropas på en Telnet Server-paketpoolspekare som inte är null skriver den över den och ersätter den befintliga paketpoolen med paketpoolen som pekaren på.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet-serverkontrollblocket
- **packet_pool_ptr:** Pekare till paketpool som skapats tidigare

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Konfigurerad pool.
- NX_PTR_ERROR: (0x07) Ogiltig server-pekare.

### <a name="allowed-from"></a>Tillåts från

Init, Threads

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

Starta en Telnet-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Description

Den här tjänsten startar en Telnet Server-instans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet Server-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Har startats.
- **NX_TELNET_NO_PACKET_POOL**: (0xF6) Ingen paketpool har angetts
- NX_PTR_ERROR: (0x07) Ogiltig server-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Stoppa en Telnet-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar en tidigare skapad och startad Telnet Server-instans.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr:** Pekare till Telnet Server-kontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Har stoppats
- NX_PTR_ERROR: (0x07) Ogiltig server-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare av tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```