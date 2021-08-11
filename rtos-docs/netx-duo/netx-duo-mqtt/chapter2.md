---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo MQTT-klient
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Duo MQTT-klientkomponenten.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: faf9d84b8b2bce12a99a72198a396b121055a8eef975349f53833a180092e0a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797542"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo MQTT-klient

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo MQTT-klientkomponenten.

## <a name="product-distribution"></a>Produktdistribution

MQTT-klienten för NetX Duo finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller två källfiler, en inkluderad fil och en fil som innehåller det här dokumentet, enligt följande:

- **nxd_mqtt_client.h** Rubrikfil för MQTT-klienten för NetX Duo
- **nxd_mqtt_client.c** C-källfil för MQTT-klienten för NetX Duo
- **nxd_mqtt_client.pdf** Beskrivning av MQTT-klienten för NetX Duo
- **demo_mqtt_client.c** NetX Duo MQTT-demonstration

## <a name="mqtt-client-installation"></a>MQTT-klientinstallation

För att kunna använda MQTT-klienten för NetX Duo ska hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\arm7\green*" måste *nxd_mqtt_client.h* och *nxd_mqtt_client.c för* NetX Duo MQTT-klienten kopieras till den här katalogen.

## <a name="using-mqtt-client"></a>Använda MQTT-klient

Det är enkelt att använda MQTT Client för NetX Duo. I princip måste programkoden innehålla *nxd_mqtt_client.h* efter att den innehåller *tx_api.h* och *nx_api.h*, för att kunna använda ThreadX respektive NetX Duo. När MQTT-klienthuvudfilerna har inkluderats kan programkoden sedan använda de MQTT-tjänster som beskrivs senare i den här guiden. Programmet måste också inkludera *nxd_mqtt_client.c* i byggprocessen. Dessa filer måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX Duo MQTT-klienten.

## <a name="using-mqtt-client-with-netx-secure-tls"></a>Använda MQTT-klienten med NetX Secure TLS

Om du vill använda MQTT-klienten med NetX Secure TLS-modulen måste programmet ha NetX Secure TLS-modulen installerad och inkludera *nx_secure_tls_api.h* *och nx_crypto.h*. MQTT-biblioteket måste byggas med symbolen ***NX_SECURE_ENABLE*** definierad.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa MQTT-klienten för NetX Duo. Nedan visas en lista över alla alternativ, där vart och ett beskrivs i detalj. Standardvärdena visas, men kan definieras om innan du tar med *nxd_mqtt_client.h.*

- **NX_DISABLE_ERROR_CHECKING**: Det här alternativet tar bort den grundläggande MQTT-klientfelkontrollen. Det används vanligtvis när programmet har felsökts.
- **NX_SECURE_ENABLE:** MQTT-klienten har definierats med TLS-stöd.
För att definiera den här symbolen måste NetX Secure TLS-modulen vara installerad.
*NX_SECURE_ENABLE* är inte aktiverat som standard.**
- **NXD_MQTT_REQUIRE_TLS:** Definierad måste programmet använda TLS för att ansluta till MQTT-meddelandekö. Den här funktionen *kräver NX_SECURE_ENABLE* definieras. Som standard definieras inte den här symbolen.
- **NXD_MQTT_MAXIMUM_TRANSMIT_QUEUE_DEPTH:** Definierad är MQTT-överföringsködjup aktiverat. Det måste vara ett positivt heltal.
- **NXD_MQTT_MAX_TOPIC_NAME_LENGTH:** Inaktuell.
- **NXD_MQTT_MAX_MESSAGE_LENGTH:** Inaktuell.
- **NXD_MQTT_KEEPALIVE_TIMER_RATE:** Definierar MQTT-timerhastigheten i ThreadX-timern tick. Den här timern används för att hålla reda på tiden sedan det senaste MQTT-kontrollmeddelandet skickades och skickar ett MQTT PINGREQ-meddelande innan keep-alive-tiden upphör att gälla. Den här timern aktiveras om klienten ansluter till koordinatorn med ett anställt keep-alive-timervärde. Standardvärdet är TX_TIMER_TICKS_PER_SECOND, vilket är en en sekunds timer.
- **NXD_MQTT_PING_TIMEOUT_DELAY:** Definierar den tid som MQTT-klienten väntar på PINGRESP från den a broker som skickas ut till MQTT PINGREQ. Om ingen PINGRESP tas emot efter den här timeout-fördröjningen behandlar klienten den a broker som icke-responsiv och kopplar bort sig själv från den a broker. Standardfördröjningen för PING TX_TIMER_TICKS_PER_SECOND, vilket är en sekund.
- **NXD_MQTT_SOCKET_TIMEOUT:** Definierar time out i TCP socket disconnect-anropet när du kopplar från MQTT-servern i timern tick. Standardvärdet är NX_WAIT_FOREVER.

## <a name="sample-mqtt-program"></a>Exempel på MQTT-program

Följande program illustrerar ett enkelt MQTT-program. För enkelhetens skull antas returkoderna lyckas, och därför utförs ingen ytterligare felkontroll.

```c
#define LOCAL_SERVER_ADDRESS (IP_ADDRESS(192, 168, 1, 81))

/*******************************************************/
/* IOT MQTT Client Example                             */
/*******************************************************/
#define DEMO_STACK_SIZE 2048
#define CLIENT_ID_STRING "mytestclient"
#define MQTT_CLIENT_STACK_SIZE 4096
#define STRLEN(p) (sizeof(p) - 1)

/* Declare the MQTT thread stack space. */
static ULONG mqtt_client_stack[MQTT_CLIENT_STACK_SIZE / sizeof(ULONG)];

/* Declare the MQTT client control block. */
static NXD_MQTT_CLIENT mqtt_client;

/* Define the symbol for signaling a received message. */

/* Define the test threads. */

#define TOPIC_NAME "topic"

#define MESSAGE_STRING "This is a message. "

/* Define the priority of the MQTT internal thread. */
#define MQTT_THREAD_PRIORTY 2

/* Define the MQTT keep alive timer for 5 minutes */
#define MQTT_KEEP_ALIVE_TIMER 300
#define QOS0 0
#define QOS1 1

/* Declare event flag, which is used in this demo. */
TX_EVENT_FLAGS_GROUP mqtt_app_flag;
#define DEMO_MESSAGE_EVENT 1
#define DEMO_ALL_EVENTS 3

/* Declare buffers to hold message and topic. */
static UCHAR message_buffer[NXD_MQTT_MAX_MESSAGE_LENGTH];
static UCHAR topic_buffer[NXD_MQTT_MAX_TOPIC_NAME_LENGTH];

/* Declare the disconnect notify function. */
static VOID my_disconnect_func(NXD_MQTT_CLIENT *client_ptr)
{
    printf("client disconnected from server\n");
}

static VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr, UINT number_of_messages)
{
    tx_event_flags_set(&mqtt_app_flag, DEMO_MESSAGE_EVENT, TX_OR);
    return;
}

static ULONG error_counter;
void demo_mqtt_client_local(NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr)
{
    UINT status;
    NXD_ADDRESS server_ip;
    ULONG events;
    UINT topic_length, message_length;

    /* Create MQTT client instance. */
    nxd_mqtt_client_create(&mqtt_client, "my_client",
        CLIENT_ID_STRING, STRLEN(CLIENT_ID_STRING), ip_ptr, pool_ptr,
        (VOID*)mqtt_client_stack, sizeof(mqtt_client_stack),
        MQTT_THREAD_PRIORTY, NX_NULL, 0);

    /* Register the disconnect notification function. */
    nxd_mqtt_client_disconnect_notify_set(&mqtt_client, my_disconnect_func);

    /* Create an event flag for this demo. */
    status = tx_event_flags_create(&mqtt_app_flag, "my app event");
    server_ip.nxd_ip_version = 4;
    server_ip.nxd_ip_address.v4 = LOCAL_SERVER_ADDRESS;

    /* Start the connection to the server. */
    nxd_mqtt_client_connect(&mqtt_client, &server_ip, NXD_MQTT_PORT, 
        MQTT_KEEP_ALIVE_TIMER, 0, NX_WAIT_FOREVER);

    /* Subscribe to the topic with QoS level 0. */
    nxd_mqtt_client_subscribe(&mqtt_client, TOPIC_NAME, STRLEN(TOPIC_NAME),
        QOS0);

    /* Set the receive notify function. */
    nxd_mqtt_client_receive_notify_set(&mqtt_client, my_notify_func);

    /* Publish a message with QoS Level 1. */
    nxd_mqtt_client_publish(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME), (CHAR*)MESSAGE_STRING, 
        STRLEN(MESSAGE_STRING), 0, QOS1, NX_WAIT_FOREVER);

    /* Now wait for the broker to publish the message. */
    tx_event_flags_get(&mqtt_app_flag, DEMO_ALL_EVENTS,
        TX_OR_CLEAR, &events, TX_WAIT_FOREVER);

    if(events & DEMO_MESSAGE_EVENT)
    {
        nxd_mqtt_client_message_get(&mqtt_client, topic_buffer,
            sizeof(topic_buffer), &topic_length, message_buffer,
            sizeof(message_buffer), &message_length);

        topic_buffer[topic_length] = 0;

        message_buffer[message_length] = 0;

        printf("topic = %s, message = %s\n", topic_buffer, message_buffer);
    }

    /* Now unsubscribe the topic. */
    nxd_mqtt_client_unsubscribe(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME));

    /* Disconnect from the broker. */
    nxd_mqtt_client_disconnect(&mqtt_client);

    /* Delete the client instance, release all the resources. */
    nxd_mqtt_client_delete(&mqtt_client);
    return;
}
```
