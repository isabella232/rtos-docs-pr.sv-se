---
title: Bilaga D – Azure RTOS NetX BSD-Compatible Socket API
description: Läs mer om BSD-Compatible Socket API för IPv4.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bd4a35c19cd794a5135f01abe5595456d39b5306ba25ce2966c3bb1aea14ea17
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790096"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a>Bilaga D – Azure RTOS NetX BSD-Compatible Socket API

## <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible Socket

Socket-API:et för BSD-Compatible stöder en delmängd av API-anropen för BSD Sockets (med vissa begränsningar) genom att använda Azure RTOS NetX-primitiver under. IPv4-protokoll och nätverksadressering stöds. Det BSD-Compatible Sockets API-lagret bör fungera lika snabbt eller något snabbare än typiska BSD-implementeringar eftersom det här API:et använder interna NetX-primitiver och kringgår onödig NetX-felkontroll.

Konfigurerbara alternativ gör att värdprogrammet kan definiera det maximala antalet sockets, tcp maximal fönsterstorlek och djup för lyssnande kö.

På grund av prestanda- och arkitekturbegränsningar stöder BSD-Compatible Sockets API inte alla BSD Sockets-anrop. Dessutom är inte alla BSD-alternativ tillgängliga för BSD-tjänsterna, särskilt följande:

- Funktionen ***select** _ fungerar endast med _fd_set readfds*, andra argument i det här anropet, \* t.ex. *writefds*, *exceptfds* stöds inte.
- Argumentet *int flags* stöds inte för funktionerna ***send** _, _*_recv_*_, _*_sendto och_*_ _ *_recvfrom_** . Det BSD-Compatible Socket-API:et stöder endast en begränsad uppsättning BSD Sockets-anrop.

Källkoden är utformad för enkelhetens skull och består endast av två filer,***nx_bsd.c** _ _*_och nx_bsd.h_*_. Installationen kräver att dessa två filer läggs till i byggprojektet (inte NetX-biblioteket) och att värdprogrammet skapas som använder BSD Socket-tjänstanrop. Filen _ *_nx_bsd.h_** måste också ingå i programkällan. Exempeldemofiler ingår i distributionen som är fritt tillgänglig med NetX. Mer information finns i hjälpen för BSD-Compatible Socket API **417** och Readme-filer som paketeras med BSD-Compatible Socket API-paketet.

Det BSD-Compatible Sockets-API:et stöder följande API-anrop för BSD Sockets:

```C
*INT bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool,
    CHAR *bsd_memory_not_used);*

*INT getpeername( INT sockID, struct sockaddr *remoteAddress, INT *addressLength);*

*INT getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);*

*INT recvfrom(INT sockID, CHAR *buffer, INT buffersize,
    INT flags,struct sockaddr *fromAddr, INT *fromAddrLen);*

*INT recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);*

*INT sendto(INT sockID, CHAR *msg, INT msgLength, INT flags,
    struct sockaddr *destAddr, INT destAddrLen);*

*INT send(INT sockID, const CHAR *msg, INT msgLength, INT flags);*

 *INT accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);*

*INT listen(INT sockID, INT backlog);*

*INT bind (INT sockID, struct sockaddr *localAddress, INT addressLength);*

*INT connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);*

*INT socket( INT protocolFamily, INT type, INT protocol);*

*INT soc_close ( INT sockID);*

*INT select(INT nfds, fd_set *readfds, fd_set *writefds,
    fd_set *exceptfds, struct timeval *timeout);*

*VOID FD_SET(INT fd, fd_set *fdset);*

*VOID FD_CLR(INT fd, fd_set *fdset);*

*INT FD_ISSET(INT fd, fd_set *fdset);*

*VOID FD_ZERO(fd_set *fdset);*

```
