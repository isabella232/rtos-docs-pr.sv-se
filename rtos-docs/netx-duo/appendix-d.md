---
title: Bilaga D – Azure RTOS NetX Duo BSD-Compatible Socket API
description: Läs mer om BSD-Compatible Socket API för IPv4 och IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd43c3efa18dd76f6eb996c84091024f48ad65aa5839958066161080dc02127e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789756"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>Bilaga D – Azure RTOS NetX Duo BSD-Compatible Socket API

## <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible Socket 
Det BSD-Compatible Socket-API:et stöder en delmängd av API-anropen för BSD Sockets (med vissa begränsningar) genom att använda NetX &reg; Duo-primitiverna under. Både IPv6- och IPv4-protokoll och nätverksadressering stöds. Det BSD-Compatible Sockets API-lagret bör fungera lika snabbt eller något snabbare än typiska BSD-implementeringar eftersom det här API:et använder interna NetX Duo-primitiver och kringgår onödig NetX-felkontroll.  

Konfigurerbara alternativ gör att värdprogrammet kan definiera det maximala antalet sockets, tcp maximal fönsterstorlek och djup för lyssnande kö.

På grund av prestanda- och arkitekturbegränsningar stöder BSD-Compatible Sockets API inte alla BSD Sockets-anrop. Dessutom är inte alla BSD-alternativ tillgängliga för BSD-tjänsterna, särskilt följande:

  - ***select** _ call fungerar endast med fd_set readfds, andra argument i det här anropet, \_ t.ex. writefds, exceptfds stöds inte.
  - Argumentet "int flags" stöds inte för ***skicka** _, _*_recv_*_, _*_sendto och_*_ _ *_recvfrom_** anrop. 
  - Det BSD-Compatible Socket-API:et stöder endast en begränsad uppsättning BSD Sockets-anrop.

Källkoden är utformad för enkelhetens skull och består av endast två filer, ***nxd_bsd.c** _ _*_och nxd_bsd.h_*_. Installationen kräver att dessa två filer läggs till i byggprojektet (inte NetX-biblioteket) och att värdprogrammet skapas som använder BSD Socket-tjänstanrop. Filen _ *_nxd_bsd.h_** måste också ingå i programkällan. Exempel på demofiler för både IPv4- och IPv6-baserade program ingår i distributionen som är fritt tillgänglig med NetX Duo. Mer information finns i hjälp- och Viktigt-filer som paketeras med API-paketet BSDCompatible Socket.

Det BSD-Compatible Sockets-API:et stöder följande API-anrop för BSD Sockets:

```c
INT     bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool, CHAR
        *bsd_memory_not_used);
```
```c
INT     getpeername( INT sockID, struct sockaddr *remoteAddress, INT
        *addressLength);
```
```c
INT     getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);
```
```c
INT     recvfrom(INT sockID, CHAR *buffer, INT buffersize, INT flags,struct sockaddr
        *fromAddr, INT *fromAddrLen);
```
```c        
INT     recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);
```
```c
INT     sendto(INT sockID, CHAR *msg, INT msgLength, INT flags, struct sockaddr
        *destAddr, INT destAddrLen);
```
```c        
INT     send(INT sockID, const CHAR *msg, INT msgLength, INT flags);
```
```c
INT     accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);
```
```c
INT     listen(INT sockID, INT backlog);
```
```c
INT     bind (INT sockID, struct sockaddr *localAddress, INT addressLength);
```
```c
INT     connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);
```
```c
INT     socket( INT protocolFamily, INT type, INT protocol);
```
```c
INT     soc_close ( INT sockID);
```
```c
INT     select(INT nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct
        timeval *timeout);
```
```c
VOID    FD_SET(INT fd, fd_set *fdset);
```
```c
VOID    FD_CLR(INT fd, fd_set *fdset);
```
```c
INT     FD_ISSET(INT fd, fd_set *fdset);
```
```c
VOID    FD_ZERO(fd_set *fdset);
```