---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX POP3
description: NetX Duo POP3-klientens API är utformat för att tillhandahålla ett e-postöverförings system för små arbets stationer för att få åtkomst till klient post-släpp på POP3-servrar för att hämta klient mail.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4d41da1e1e87e59c5c40674a58b288ac62ec8c78
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825848"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3"></a><span data-ttu-id="54ba1-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX POP3</span><span class="sxs-lookup"><span data-stu-id="54ba1-103">Chapter 1 - Introduction to Azure RTOS NetX POP3</span></span>

<span data-ttu-id="54ba1-104">Post Office Protocol version 3 (POP3) är ett protokoll som har utformats för att tillhandahålla ett e-postöverförings system för små arbets stationer för att få åtkomst till klient post-släpp på POP3-servrar för att hämta klient mail.</span><span class="sxs-lookup"><span data-stu-id="54ba1-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="54ba1-105">POP3 använder Transmission Control Protocol (TCP)-tjänster för att utföra e-postöverföring.</span><span class="sxs-lookup"><span data-stu-id="54ba1-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="54ba1-106">Därför är POP3 ett mycket tillförlitligt innehålls överförings protokoll.</span><span class="sxs-lookup"><span data-stu-id="54ba1-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="54ba1-107">POP3 tillhandahåller dock inte omfattande åtgärder vid e-posthantering.</span><span class="sxs-lookup"><span data-stu-id="54ba1-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="54ba1-108">Vanligt vis hämtas mail av klienten och tas sedan bort från serverns maildrop.</span><span class="sxs-lookup"><span data-stu-id="54ba1-108">Typically, mail is downloaded by the Client and then deleted from the Server’s maildrop.</span></span>

## <a name="netx-duo-pop3-client-requirements"></a><span data-ttu-id="54ba1-109">NetX Duo POP3-klient krav</span><span class="sxs-lookup"><span data-stu-id="54ba1-109">NetX Duo POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="54ba1-110">Klient krav</span><span class="sxs-lookup"><span data-stu-id="54ba1-110">Client Requirements</span></span>

<span data-ttu-id="54ba1-111">NetX POP3 client API kräver en tidigare skapad NetX Duo IP-instans med *nx_ip_create* och en tidigare skapad netx-adresspool med *nx_packet_pool_create*.</span><span class="sxs-lookup"><span data-stu-id="54ba1-111">The NetX POP3 Client API requires a previously created NetX Duo IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="54ba1-112">Eftersom NetX Duo-klienten använder TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* anropet innan du använder netx Duo POP3-klient-API: et på samma IP-instans.</span><span class="sxs-lookup"><span data-stu-id="54ba1-112">Because the NetX Duo POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX Duo POP3 Client API on that same IP instance.</span></span> <span data-ttu-id="54ba1-113">POP3-klienten använder en TCP-socket för att ansluta till en POP3-server på serverns POP3-port.</span><span class="sxs-lookup"><span data-stu-id="54ba1-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server’s POP3 port.</span></span> <span data-ttu-id="54ba1-114">Detta anges vanligt vis på den *välkända porten 110, men ingen POP3-klient eller server krävs för att använda den här porten.*</span><span class="sxs-lookup"><span data-stu-id="54ba1-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server are required to use this port.*</span></span>

<span data-ttu-id="54ba1-115">Storleken på den modempool som används för att skapa POP3-klienten är en användare som kan konfigureras i form av paketets nytto last och antalet tillgängliga paket.</span><span class="sxs-lookup"><span data-stu-id="54ba1-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="54ba1-116">Om paketet bara används i POP3-klienten för att skapa, behöver paketets nytto last inte vara mer än 100-120 byte beroende på användar namn och lösen ord, eller APOP Digest.</span><span class="sxs-lookup"><span data-stu-id="54ba1-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="54ba1-117">ANVÄNDAR kommandot med den lokala värdens användar namn är förmodligen det största meddelande som skickas av POP3-klienten.</span><span class="sxs-lookup"><span data-stu-id="54ba1-117">The USER command with the local host’s user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="54ba1-118">Det går att dela samma adresspool i nx_ip_create (IP-standardpool) eftersom den interna IP-operatiosn inte kräver mycket stor paket nytto last för att skicka och ta emot TCP-kontroll data.</span><span class="sxs-lookup"><span data-stu-id="54ba1-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operatiosn do not require very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="54ba1-119">Men det är inte allmänt fördelaktigt för Ethernet-drivrutinen att använda samma modempool som POP3-klientens adresspool.</span><span class="sxs-lookup"><span data-stu-id="54ba1-119">However, it is not generally advantageous for the Ethernet driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="54ba1-120">I allmänhet ställer nytto lasten i nytto lasten för inhämtade paket till IP-instansen MTU (vanligt vis 1500 byte) av nätverks gränssnittet som är mycket större än POP3-klient meddelanden.</span><span class="sxs-lookup"><span data-stu-id="54ba1-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="54ba1-121">Inkommande POP3-meddelanden skulle normalt vara mycket större data storlek och utgående POP3-klient meddelanden</span><span class="sxs-lookup"><span data-stu-id="54ba1-121">Incoming POP3 messages would usually be much larger data size then outgoing POP3 Client messages</span></span>

## <a name="netx-duo-pop3-client-creation"></a><span data-ttu-id="54ba1-122">NetX Duo POP3-klient skapande</span><span class="sxs-lookup"><span data-stu-id="54ba1-122">NetX Duo POP3 Client Creation</span></span>

<span data-ttu-id="54ba1-123">Det finns två tjänster för att skapa POP3-klienten.</span><span class="sxs-lookup"><span data-stu-id="54ba1-123">There are two services for creating the POP3 Client.</span></span> <span data-ttu-id="54ba1-124">Den rekommenderade tjänsten är *nxd_pop3_client_create* som tar en NXD_ADDRESSs adress data typ som accepterar IPv4-eller IPv6-adresser för POP3-servern.</span><span class="sxs-lookup"><span data-stu-id="54ba1-124">The recommended service is *nxd_pop3_client_create* which takes an NXD_ADDRESS address data type that accepts IPv4 or IPv6 addresses for the POP3 server.</span></span> <span data-ttu-id="54ba1-125">Den andra POP3-klienten Create service, *nx_pop3_client_create* accepterar bara IPv4-adresser för POP3-servern.</span><span class="sxs-lookup"><span data-stu-id="54ba1-125">The other POP3 Client create service, *nx_pop3_client_create*, only accepts IPv4 addresses for the POP3 server.</span></span> <span data-ttu-id="54ba1-126">Båda tjänsterna binder TCP-socket-porten och ansluter till POP3-servern.</span><span class="sxs-lookup"><span data-stu-id="54ba1-126">Both services bind the TCP socket port and connect with the POP3 server.</span></span>

<span data-ttu-id="54ba1-127">När du har anslutit till POP3-servern kan POP3-klient programmet anropa *nx_pop3_client _mail_items_get* för att hämta antalet e-postobjekt i rutan maildrop:</span><span class="sxs-lookup"><span data-stu-id="54ba1-127">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items, ULONG *maildrop_total_size);
```

<span data-ttu-id="54ba1-128">Om ett eller flera objekt finns i klientens maildrop kan programmet Hämta storleken på ett särskilt e-postobjekt med hjälp av tjänsten *nx_pop3_client_get_mail_item* :</span><span class="sxs-lookup"><span data-stu-id="54ba1-128">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

<span data-ttu-id="54ba1-129">Det första e-postobjektet i maildrop är vid index 1.</span><span class="sxs-lookup"><span data-stu-id="54ba1-129">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="54ba1-130">För att hämta det faktiska e-postmeddelandet kan programmet anropa *nx_pop3_client_mail_item_get_message_data* -tjänsten för att hämta e-postmeddelande paketen tills tjänsten anger att det sista paketet tas emot final_packet av argumentet indatamängd:</span><span class="sxs-lookup"><span data-stu-id="54ba1-130">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

<span data-ttu-id="54ba1-131">Om du vill ta bort ett särskilt e-postobjekt anropar programmet *nx_pop3_client_mail_item_delete* med samma index som används i föregående *nx_pop3_client_get_mail_item* anrop.</span><span class="sxs-lookup"><span data-stu-id="54ba1-131">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="54ba1-132">Klienten kan tas bort med hjälp av tjänsten *nx_pop3_client_delete* .</span><span class="sxs-lookup"><span data-stu-id="54ba1-132">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="54ba1-133">Observera att det är upp till programmet att ta bort POP3-anslutningspoolen med hjälp av *nx_packet_pool_delete* -tjänsten där den inte längre används.</span><span class="sxs-lookup"><span data-stu-id="54ba1-133">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-duo-pop3-client-constraints"></a><span data-ttu-id="54ba1-134">NetX Duo POP3-klient begränsningar</span><span class="sxs-lookup"><span data-stu-id="54ba1-134">NetX Duo POP3 Client Constraints</span></span>

<span data-ttu-id="54ba1-135">Det finns vissa begränsningar i NetX Duo POP3-klient implementeringen:</span><span class="sxs-lookup"><span data-stu-id="54ba1-135">There are some constraints in the NetX Duo POP3 Client implementation:</span></span>

1. <span data-ttu-id="54ba1-136">NetX Duo POP3-klienten har inte stöd för kommandot AUTH, men den implementerar APOP-autentisering med DIGEST-MD5 för Exchange-autentisering av klientautentisering.</span><span class="sxs-lookup"><span data-stu-id="54ba1-136">The NetX Duo POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>
2. <span data-ttu-id="54ba1-137">NetX Duo POP3-klienten implementerar inte alla POP3-kommandon (t. ex. TOP-eller UIDL-kommandon).</span><span class="sxs-lookup"><span data-stu-id="54ba1-137">NetX Duo POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="54ba1-138">Nedan visas en lista med kommandon som stöder:</span><span class="sxs-lookup"><span data-stu-id="54ba1-138">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="54ba1-139">NOOP</span><span class="sxs-lookup"><span data-stu-id="54ba1-139">NOOP</span></span>
   - <span data-ttu-id="54ba1-140">RSET</span><span class="sxs-lookup"><span data-stu-id="54ba1-140">RSET</span></span>

## <a name="netx-duo-pop3-client-login"></a><span data-ttu-id="54ba1-141">NetX Duo POP3-klient inloggning</span><span class="sxs-lookup"><span data-stu-id="54ba1-141">NetX Duo POP3 Client Login</span></span>

<span data-ttu-id="54ba1-142">En NetX Duo POP3-klient måste autentisera sig själv (inloggning) till en POP3-server för att få åtkomst till en maildrop.</span><span class="sxs-lookup"><span data-stu-id="54ba1-142">A NetX Duo POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="54ba1-143">Det kan göra detta antingen genom att använda användar-/PASS-kommandon och ange användar namn och lösen ord som är kända för POP3-servern, eller med hjälp av kommandot APOP och MD5 Digest som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="54ba1-143">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="54ba1-144">Användar namnet är vanligt vis ett fullständigt kvalificerat domän namn (innehåller en lokal del och ett domän namn, avgränsat med ett @-värde).</span><span class="sxs-lookup"><span data-stu-id="54ba1-144">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an ‘@’ character).</span></span> <span data-ttu-id="54ba1-145">När du använder POP3-kommandona användare och PASS skickar klienten sitt användar namn och lösen ord okrypterat via Internet.</span><span class="sxs-lookup"><span data-stu-id="54ba1-145">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="54ba1-146">För att undvika säkerhets risken för klartext och lösen ord för text, kan NetX Duo POP3-klienten konfigureras att använda APOP-autentisering genom att ange parametern *APOP_authentication* i *nxd_pop3_client_create* -tjänsten:</span><span class="sxs-lookup"><span data-stu-id="54ba1-146">To avoid the security risk of clear texting username and password, the NetX Duo POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nxd_pop3_client_create* service:</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address, ULONG server_port,
    CHAR *client_name,
    CHAR *client_password);
```

<span data-ttu-id="54ba1-147">*Nx_pop3_client_create* tjänsten för endast IPv4-program:</span><span class="sxs-lookup"><span data-stu-id="54ba1-147">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```C
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address,
    ULONG server_port, CHAR *client_name,
    CHAR *client_password);
```

<span data-ttu-id="54ba1-148">När klienten skickar kommandot APOP tar det bara en MD5-Digest som innehåller Server domänen, lokal tid och process-ID som extraheras från serverns hälsning, plus klientens lösen ord.</span><span class="sxs-lookup"><span data-stu-id="54ba1-148">When the Client sends the APOP command, it takes as its only argument an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="54ba1-149">POP3-servern skapar en MD5-Digest som innehåller samma information och om dess MD5-Digest matchar klientens MD5-Digest, autentiseras klienten.</span><span class="sxs-lookup"><span data-stu-id="54ba1-149">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client’s MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="54ba1-150">Om APOP-autentiseringen Miss lyckas, kommer NetX Duo POP3-klienten att försöka USER/PASS-autentisering.</span><span class="sxs-lookup"><span data-stu-id="54ba1-150">If APOP authentication fails, NetX Duo POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="54ba1-151">POP3-maildrop</span><span class="sxs-lookup"><span data-stu-id="54ba1-151">The POP3 Client Maildrop</span></span>

<span data-ttu-id="54ba1-152">Klientens e-post lagras på en POP3-server i en post låda eller "maildrop".</span><span class="sxs-lookup"><span data-stu-id="54ba1-152">Client mail is stored on a POP3 Server in a mailbox or “maildrop.”</span></span> <span data-ttu-id="54ba1-153">En klient-maildrop på en POP3-server representeras som en 1-baserad lista över e-postobjekt.</span><span class="sxs-lookup"><span data-stu-id="54ba1-153">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="54ba1-154">Det vill säga att varje post refereras till av sitt index i maildrop-listan med det första e-postobjektet vid index 1 (inte noll).</span><span class="sxs-lookup"><span data-stu-id="54ba1-154">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="54ba1-155">POP3-kommandon refererar till vissa e-postobjekt baserat på deras index i den här listan.</span><span class="sxs-lookup"><span data-stu-id="54ba1-155">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="54ba1-156">Tillstånds datorn för POP3-protokollet</span><span class="sxs-lookup"><span data-stu-id="54ba1-156">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="54ba1-157">POP3-protokollet kräver att både klienten och servern behåller status för POP3-sessionen.</span><span class="sxs-lookup"><span data-stu-id="54ba1-157">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="54ba1-158">Först försöker klienten ansluta till POP3-servern.</span><span class="sxs-lookup"><span data-stu-id="54ba1-158">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="54ba1-159">Om det lyckas går det in i POP3-protokollet som har tre distinkta tillstånd definierade av RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="54ba1-159">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="54ba1-160">Start tillståndet är det tillstånd där det måste identifiera sig för servern.</span><span class="sxs-lookup"><span data-stu-id="54ba1-160">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="54ba1-161">I tillståndet Authorization kan POP3-klienten endast utfärda användare och PASS-kommandon, i den ordningen eller kommandot APOP.</span><span class="sxs-lookup"><span data-stu-id="54ba1-161">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="54ba1-162">När POP3-klienten har autentiserats, anger klientens session transaktions statusen.</span><span class="sxs-lookup"><span data-stu-id="54ba1-162">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="54ba1-163">I det här läget kan klienten Ladda ned och begära borttagning av e-post.</span><span class="sxs-lookup"><span data-stu-id="54ba1-163">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="54ba1-164">De kommandon som tillåts i transaktions tillstånd är LIST, STAT, RETR, &, RSET och avsluta.</span><span class="sxs-lookup"><span data-stu-id="54ba1-164">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="54ba1-165">Normalt skickar POP3-klienten ett STAT-kommando följt av en serie med RETR-kommandon (en för varje e-postobjekt i dess maildrop).</span><span class="sxs-lookup"><span data-stu-id="54ba1-165">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="54ba1-166">När klienten utfärdar kommandot QUIT, anger POP3-sessionen det uppdaterings tillstånd där den initierar TCP-från koppling från servern.</span><span class="sxs-lookup"><span data-stu-id="54ba1-166">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="54ba1-167">För att hämta e-post vid en annan tidpunkt kan POP3-klient programmet anropa nx_pop3_client_mail_items_get för att söka efter ny e-post i maildrop.</span><span class="sxs-lookup"><span data-stu-id="54ba1-167">To download mail at another time, the POP3 Client application can call nx_pop3_client_mail_items_get to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="54ba1-168">Svars koder för POP3-server</span><span class="sxs-lookup"><span data-stu-id="54ba1-168">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="54ba1-169">+ OK servern använder det här svaret för att acceptera ett klient kommando.</span><span class="sxs-lookup"><span data-stu-id="54ba1-169">+OK The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="54ba1-170">Servern kan innehålla ytterligare information efter "+ OK" men det går inte att anta att klienten bearbetar informationen, förutom vid hämtning av e-postmeddelande data eller LIST-eller &-kommandon.</span><span class="sxs-lookup"><span data-stu-id="54ba1-170">The Server can include additional information after the ‘+OK’ but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="54ba1-171">I det senare fallet refererar argumentet efter kommandot till indexet för e-postobjektet i-klientens maildrop.</span><span class="sxs-lookup"><span data-stu-id="54ba1-171">In the latter case, the ‘argument’ after the command references the index of the mail item in the Client maildrop.</span></span>
- <span data-ttu-id="54ba1-172">-FEL servern använder det här svaret för att avvisa ett klient kommando.</span><span class="sxs-lookup"><span data-stu-id="54ba1-172">-ERR The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="54ba1-173">Servern kan skicka ytterligare information efter "-ERR", men kan inte förutsätta att klienten bearbetar den här informationen.</span><span class="sxs-lookup"><span data-stu-id="54ba1-173">The Server may send additional information following the ‘-ERR’ but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="54ba1-174">Exempel på POP3-klient-server-session</span><span class="sxs-lookup"><span data-stu-id="54ba1-174">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="54ba1-175">**Grundläggande POP3-exempel som använder USER/PASS:**</span><span class="sxs-lookup"><span data-stu-id="54ba1-175">**Basic POP3 example using USER/PASS:**</span></span>

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

<span data-ttu-id="54ba1-176">**Grundläggande POP3-exempel med APOP (och lista i stället för STAT):**</span><span class="sxs-lookup"><span data-stu-id="54ba1-176">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-duo-pop3-client"></a><span data-ttu-id="54ba1-177">RFC: er som stöds av NetX Duo POP3-klienten</span><span class="sxs-lookup"><span data-stu-id="54ba1-177">RFCs Supported by NetX Duo POP3 Client</span></span>

<span data-ttu-id="54ba1-178">NetX Duo-klienten POP3 är kompatibel med RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="54ba1-178">NetX Duo Client POP3 is compliant with RFC 1939.</span></span>
