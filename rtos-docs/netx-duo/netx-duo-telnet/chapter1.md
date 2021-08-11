---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo Telnet
description: Den Azure RTOS NetX Duo Telnet är ett protokoll som utformats för att överföra kommandon och svar mellan två noder på Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50a2c4d8726863f4e609debadd9ddf2455cfd540219a476970756d3d250ec562
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799038"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo Telnet

Den Azure RTOS NetX Duo Telnet är ett protokoll som utformats för att överföra kommandon och svar mellan två noder på Internet. Telnet är ett enkelt protokoll som använder tillförlitliga Transmission Control Protocol (TCP)-tjänster för att utföra sin överföringsfunktion. Därför är Telnet ett mycket tillförlitligt överföringsprotokoll. Telnet är också ett av de mest använda programprotokollen.

## <a name="telnet-requirements"></a>Telnet-krav

NetX Duo Telnet-paketet kräver att en NetX IP-instans redan har skapats för att fungera korrekt. Dessutom måste TCP vara aktiverat på samma IP-instans. Telnet-klientdelen av NetX Duo Telnet-paketet har inga ytterligare krav.

Telnet-serverdelen av NetX Duo Telnet-paketet har ytterligare ett krav. Den kräver fullständig åtkomst till TCP *välkänd port 23 för hantering* av alla klient-Telnet-begäranden.

## <a name="telnet-constraints"></a>Begränsningar för Telnet 

NetX Duo Telnet-protokollet implementerar Telnet-standarden. Tolkning och svar av Telnet-kommandon, som anges av en byte med värdet 255, är dock programmets ansvar. De olika Telnet-kommandona och kommandoparametrarna definieras *i filerna nxd_telnet_client.h och nxd_telnet_server.h.*

## <a name="telnet-communication"></a>Telnet-kommunikation

Som tidigare nämnts använder Telnet-servern den välkända *TCP-port 23 för* fältet Klientbegäranden. Telnet-klienter kan använda valfri tillgänglig TCP-port.

## <a name="telnet-authentication"></a>Telnet-autentisering

Telnet-autentisering är ansvaret för programmets Telnet Server-återanropsfunktion. Programmets återanrop till Telnet Server "ny anslutning" uppmanar vanligtvis klienten att ange namn och/eller lösenord. Klienten skulle då ansvara för att tillhandahålla informationen. Servern bearbetar sedan informationen i motringningen "ta emot data". Det är här som programserverkoden måste autentisera informationen och avgöra om den är giltig eller inte.

## <a name="telnet-new-connection-callback"></a>Telnet – återanrop av anslutning

NetX Duo Telnet Server anropar den programangivna återanropsfunktionen när en ny Telnet-klientbegäran tas emot. Programmet anger återanropsfunktionen när Telnet-servern skapas via nx_telnet_server_create ***funktionen.*** Vanliga åtgärder för återanropet "ny anslutning" är att skicka en banderoll eller en uppmaning till klienten. Detta kan mycket väl innehålla en uppmaning om inloggningsinformation.

### <a name="prototype"></a>Prototyp

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: Pekare till den anropande Telnet-servern.
- **logical_connection:** Den interna logiska anslutningen för Telnet-servern. Detta kan användas av programmet som ett index i buffertar och/eller datastrukturer som är specifika för varje klientanslutning. Värdet sträcker sig från 0 till NX_TELNET_MAX_CLIENTS – 1.

## <a name="telnet-receive-data-callback"></a>Återanrop för Telnet-mottagningsdata

NetX Duo Telnet Server anropar den programangivna återanropsfunktionen när nya Telnet-klientdata tas emot. Programmet anger återanropsfunktionen när Telnet-servern skapas via nx_telnet_server_create ***funktionen.*** Vanliga åtgärder för återanropet "ny anslutning" omfattar att upprepa data tillbaka och/eller parsa data och tillhandahålla data som ett resultat av att tolka ett kommando från klienten.

Observera att den här återanropsrutinen också måste släppa det angivna paketet.

### <a name="prototype"></a>Prototyp

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: Pekare till den anropande Telnet-servern.
- **logical_connection:** Den interna logiska anslutningen för Telnet-servern. Detta kan användas av programmet som ett index i buffertar och/eller datastrukturer som är specifika för varje klientanslutning. Värdet sträcker sig från 0 till NX_TELNET_MAX_CLIENTS – 1.
- **packet_ptr:** Pekare till paket som innehåller data från klienten.

## <a name="telnet-end-connection-callback"></a>Motringning av Telnet-slutanslutning

NetX Duo Telnet Server anropar den programangivna återanropsfunktionen när en Telnet-klient avslutar anslutningen. Programmet anger återanropsfunktionen när Telnet-servern skapas via nx_telnet_server_create ***funktionen.*** Vanliga åtgärder för återanropet "slutanslutning" omfattar rensning av klientspecifika datastrukturer som är associerade med den logiska anslutningen.

### <a name="prototype"></a>Prototyp
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till den anropande Telnet-servern.
- **logical_connection** Den interna logiska anslutningen för Telnet-servern. Detta kan användas av programmet som ett index i buffertar och/eller datastrukturer som är specifika för varje klientanslutning. Värdet sträcker sig från 0 till NX_TELNET_MAX_CLIENTS – 1.

## <a name="telnet-option-negotiation"></a>Telnet-alternativförhandling

NetX Duo Telnet Server stöder en begränsad uppsättning Telnet-alternativ, Echo och Suppress Go Ahead.

Om du vill aktivera den här NX_TELNET_SERVER_OPTION_DISABLE inte definieras. Som standard definieras den inte. Telnet-servern skapar en paketpool *i den nx_telnet_server_create-tjänst* som den tilldelar paket för att skicka telnet-alternativbegäranden till klienten. Se Konfigurationsalternativ för att ange paketnyttolasten (NX_TELNET_SERVER_PACKET_PAYLOAD) och paketpoolens storlek (NX_TELNET_SERVER_PACKET_POOL_SIZE) för den här paketpoolen. Paketpoolen tas bort när *nx_telnet_server_delete* anropas.

När en anslutning upprättas med Telnet-klienten skickas den här uppsättningen telnet-alternativ till klienten om den inte har tagit emot alternativbegäranden från klienten:

- kommer att ge eko
- upprepa inte
- kommer sga

När Telnet-data tar emot data från klienten kontrollerar Telnet-servern om den första byten är IAC-koden. I så fall bearbetas alla alternativ i klientpaketet. Alternativ som inte finns i listan ovan ignoreras.

Som standard skapar Telnet-servern sin egen interna paketpool om NX_TELNET_SERVER_OPTION_DISABLE inte har definierats och den behöver överföra Telnet-alternativkommandon. Telnet Server-paketpoolen definieras av NX_TELNET_SERVER_PACKET_PAYLOAD och NX_TELNET_SERVER_PACKET_POOLSIZE. Men om NX_TELNET_SERVER_USER_CREATE_PACKET_POOL definieras måste programmet skapa Telnet Server-paketpoolen och ange den som Telnet Server-paketpoolen genom att *anropa _nx_telnet_server_packet_pool_set*. Se kapitel 3 "Beskrivning av Telnet Services" för mer information om den här funktionen.

Till skillnad från NetX Duo Telnet Server skickar och svarar inte NetX Duo Telnet Client-uppgiftstråden automatiskt på mottagna alternativ från Telnet-servern. Detta måste göras av Telnet-klientprogrammet.

## <a name="telnet-multi-thread-support"></a>Telnet-stöd för flera trådar

NetX Duo Telnet-klienttjänsterna kan anropas från flera trådar samtidigt. Läs- eller skrivbegäranden för en viss Telnet-klientinstans bör dock göras i följd från samma tråd.

## <a name="telnet-rfcs"></a>Telnet-RFC:er

NetX Duo Telnet är kompatibelt med RFC854 och relaterade RFC: er.
