---
title: Bilaga D – Azure återställnings tider NetX BSD-Compatible socket API
description: 'Lär dig mer om API: et för BSD-Compatible socket för IPv4.'
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9062e27d8f447ac8d36e7a09afee5ac14f86f8c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826898"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a><span data-ttu-id="5b859-103">Bilaga D – Azure återställnings tider NetX BSD-Compatible socket API</span><span class="sxs-lookup"><span data-stu-id="5b859-103">Appendix D - Azure RTOS NetX BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="5b859-104">API för BSD-Compatible socket</span><span class="sxs-lookup"><span data-stu-id="5b859-104">BSD-Compatible Socket API</span></span>

<span data-ttu-id="5b859-105">API-anrop för BSD-Compatible socket har stöd för en delmängd av BSD-API-anrop (med vissa begränsningar) genom att använda Azure återställnings tider NetX-primitiver under.</span><span class="sxs-lookup"><span data-stu-id="5b859-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing Azure RTOS NetX primitives underneath.</span></span> <span data-ttu-id="5b859-106">IPv4-protokoll och nätverks adresser stöds.</span><span class="sxs-lookup"><span data-stu-id="5b859-106">IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="5b859-107">Detta API-skikt i BSD-Compatible Sockets ska fungera lika snabb eller något snabbare än vanliga BSD-implementeringar eftersom detta API använder interna NetX-primitiver och kringgår onödig fel kontroll av NetX.</span><span class="sxs-lookup"><span data-stu-id="5b859-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX primitives and bypasses unnecessary NetX error checking.</span></span>

<span data-ttu-id="5b859-108">Med konfigurerbara alternativ kan värd programmet definiera maximalt antal Sockets, maximal storlek för TCP-fönster och djup i lyssnings kön.</span><span class="sxs-lookup"><span data-stu-id="5b859-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="5b859-109">På grund av prestanda-och arkitektur begränsningar stöder detta BSD-Compatible Sockets-API: t inte alla BSD-anrop i BSD.</span><span class="sxs-lookup"><span data-stu-id="5b859-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="5b859-110">Dessutom är inte alla BSD-alternativ tillgängliga för BSD-tjänsterna, särskilt följande:</span><span class="sxs-lookup"><span data-stu-id="5b859-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

- <span data-ttu-id="5b859-111">Funktionen \***Select** _ fungerar med endast _fd_set \* readfds \*, andra argument i det här anropet, t. ex. *writefds*, *exceptfds* stöds inte.</span><span class="sxs-lookup"><span data-stu-id="5b859-111">The ***select** _ function works with only _fd_set \*readfds*, other arguments in this call e.g., *writefds*, *exceptfds* are not supported.</span></span>
- <span data-ttu-id="5b859-112">Argumentet *för int-flaggor* stöds inte för funktionerna ***send** _, _*_Recv_*_, _*_SendTo_\*_ och _ \*_recvfrom_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b859-112">The *int flags* argument is not supported for the ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** functions.</span></span> <span data-ttu-id="5b859-113">API: et för BSD-Compatible socket stöder endast en begränsad uppsättning BSD Sockets-anrop.</span><span class="sxs-lookup"><span data-stu-id="5b859-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="5b859-114">Käll koden är utformad för enkelhet och består endast av två filer, ***nx_bsd. c** _ och _*_nx_bsd. h_\*_.</span><span class="sxs-lookup"><span data-stu-id="5b859-114">The source code is designed for simplicity and is comprised of only two files,***nx_bsd.c** _ and _*_nx_bsd.h_\*_.</span></span> <span data-ttu-id="5b859-115">Installationen kräver att du lägger till de här två filerna i build-projektet (inte NetX-biblioteket) och skapar värd programmet som ska använda BSD socket service-anrop.</span><span class="sxs-lookup"><span data-stu-id="5b859-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="5b859-116">Filen _ *_nx_bsd. h_*\* måste också ingå i program källan.</span><span class="sxs-lookup"><span data-stu-id="5b859-116">The _ *_nx_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="5b859-117">Exempel på demonstrations filer ingår i distributionen som är gratis tillgänglig med NetX.</span><span class="sxs-lookup"><span data-stu-id="5b859-117">Sample demo files are included with the distribution which is freely available with NetX.</span></span> <span data-ttu-id="5b859-118">Mer information finns i hjälpen BSD-Compatible socket API **417** och readme filer som är sammankopplade med API-paketet BSD-Compatible socket.</span><span class="sxs-lookup"><span data-stu-id="5b859-118">Further details are available in the help BSD-Compatible Socket API **417** and Readme files bundled with the BSD-Compatible Socket API package.</span></span>

<span data-ttu-id="5b859-119">API: erna för BSD-Compatible Sockets stöder följande API-anrop i BSD:</span><span class="sxs-lookup"><span data-stu-id="5b859-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

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
