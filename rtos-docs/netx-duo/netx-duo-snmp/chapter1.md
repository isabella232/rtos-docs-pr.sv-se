---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SNMP
description: NetX Duo SNMP-implementeringen är en SNMP-agent. En agent ansvarar för att svara på SNMP-hanterarens kommandon och skicka händelse drivna traps.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825782"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a><span data-ttu-id="e7881-104">Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SNMP</span><span class="sxs-lookup"><span data-stu-id="e7881-104">Chapter 1 - Introduction to Azure RTOS NetX Duo SNMP</span></span>

<span data-ttu-id="e7881-105">Simple Network Management Protocol (SNMP) är ett protokoll som har utformats för att hantera enheter på Internet.</span><span class="sxs-lookup"><span data-stu-id="e7881-105">The Simple Network Management Protocol (SNMP) is a protocol designed for managing devices on the internet.</span></span> <span data-ttu-id="e7881-106">SNMP är ett protokoll som använder tjänsterna för anslutnings lös UDP (User Datagram Protocol) för att utföra sin hanterings funktion.</span><span class="sxs-lookup"><span data-stu-id="e7881-106">SNMP is a protocol that utilizes the connectionless User Datagram Protocol (UDP) services to perform its management function.</span></span> <span data-ttu-id="e7881-107">Azure återställnings tider NetX Duo SNMP-implementeringen är en SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="e7881-107">The Azure RTOS NetX Duo SNMP implementation is that of an SNMP Agent.</span></span> <span data-ttu-id="e7881-108">En agent ansvarar för att svara på SNMP-hanterarens kommandon och skicka händelse drivna traps.</span><span class="sxs-lookup"><span data-stu-id="e7881-108">An agent is responsible for responding to SNMP Manager’s commands and sending event driven traps.</span></span> 

<span data-ttu-id="e7881-109">NetX Duo SNMP stöder både IPv4-och IPv6-kommunikation med SNMP-hanterare.</span><span class="sxs-lookup"><span data-stu-id="e7881-109">NetX Duo SNMP supports both IPv4 and IPv6 communication with SNMP Managers.</span></span> <span data-ttu-id="e7881-110">NetX SNMP-program bör kompilera och köra i NetX Duo SNMP.</span><span class="sxs-lookup"><span data-stu-id="e7881-110">NetX SNMP applications should compile and run in NetX Duo SNMP.</span></span> <span data-ttu-id="e7881-111">Utvecklare uppmanas dock att Porta befintliga SNMP-program för att använda motsvarande "Duo"-tjänster.</span><span class="sxs-lookup"><span data-stu-id="e7881-111">However, the developer is encouraged to port existing SNMP applications to using the equivalent “duo” services.</span></span> <span data-ttu-id="e7881-112">Om du till exempel skickar SNMP trap-meddelanden ska följande Duo-tjänster ersätta deras NetX-motsvarighet:</span><span class="sxs-lookup"><span data-stu-id="e7881-112">For example, when sending SNMP trap messages, the following ‘duo’ services should replace their NetX equivalent:</span></span>

<span data-ttu-id="e7881-113">*nxd_snmp_object_trap_send*</span><span class="sxs-lookup"><span data-stu-id="e7881-113">*nxd_snmp_object_trap_send*</span></span>

<span data-ttu-id="e7881-114">*nxd_snmp_object_trapv2_send*</span><span class="sxs-lookup"><span data-stu-id="e7881-114">*nxd_snmp_object_trapv2_send*</span></span>

<span data-ttu-id="e7881-115">*nxd_snmp_object_trapv3_send*</span><span class="sxs-lookup"><span data-stu-id="e7881-115">*nxd_snmp_object_trapv3_send*</span></span>

<span data-ttu-id="e7881-116">Mer information finns i **Beskrivning av SNMP agent-tjänster** någon annan stans i användar handboken för mer information.</span><span class="sxs-lookup"><span data-stu-id="e7881-116">For more details, see **Description of SNMP Agent Services** elsewhere in this User Guide for more details.</span></span>

## <a name="netx-duo-snmp-agent-requirements"></a><span data-ttu-id="e7881-117">Krav för NetX Duo SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="e7881-117">NetX Duo SNMP Agent Requirements</span></span>

<span data-ttu-id="e7881-118">NetX Duo SNMP-paketet kräver att en IP-instans redan har skapats.</span><span class="sxs-lookup"><span data-stu-id="e7881-118">The NetX Duo SNMP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="e7881-119">Dessutom måste UDP vara aktiverat på samma IP-instans.</span><span class="sxs-lookup"><span data-stu-id="e7881-119">In addition, UDP must be enabled on that same IP instance.</span></span>

<span data-ttu-id="e7881-120">NetX Duo SNMP-agenten har flera ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="e7881-120">The NetX Duo SNMP Agent has several additional requirements.</span></span> <span data-ttu-id="e7881-121">Först måste den ha åtkomst till port 161 för hantering av alla SNMP Manager-begäranden.</span><span class="sxs-lookup"><span data-stu-id="e7881-121">First, it requires access to port 161 for handling all SNMP manager requests.</span></span> <span data-ttu-id="e7881-122">Det kräver också åtkomst till port 162 för att skicka trap-meddelanden till chefen.</span><span class="sxs-lookup"><span data-stu-id="e7881-122">It also requires access to port 162 for sending trap messages to the Manager.</span></span>

<span data-ttu-id="e7881-123">Om du vill använda NetX Duo SNMP-agenten med över IPv6 och för att hämta IPv6-objekt måste IPv6 vara aktiverat i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="e7881-123">To use NetX Duo SNMP Agent with over IPv6 and to obtain IPv6 objects, IPv6 must be enabled in NetX Duo.</span></span> <span data-ttu-id="e7881-124">I ***användar handboken för netx Duo*** finns mer information om hur du aktiverar IP-instansen för IPv6-tjänster.</span><span class="sxs-lookup"><span data-stu-id="e7881-124">See the ***NetX Duo User Guide*** for details on enabling the IP instance for IPv6 services.</span></span>

## <a name="netx-duo-snmp-constraints"></a><span data-ttu-id="e7881-125">NetX Duo SNMP-begränsningar</span><span class="sxs-lookup"><span data-stu-id="e7881-125">NetX Duo SNMP Constraints</span></span>

<span data-ttu-id="e7881-126">NetX Duo SNMP-protokollet implementerar SNMP version 1, 2 och 3.</span><span class="sxs-lookup"><span data-stu-id="e7881-126">The NetX Duo SNMP protocol implements SNMP Version 1, 2, and 3.</span></span> <span data-ttu-id="e7881-127">SNMPv3-implementeringen stöder MD5-och SHA-autentisering och DES-kryptering.</span><span class="sxs-lookup"><span data-stu-id="e7881-127">The SNMPv3 implementation supports MD5 and SHA authentication, and DES encryption.</span></span> <span data-ttu-id="e7881-128">Den här versionen av NetX Duo SNMP-agenten har följande begränsningar:</span><span class="sxs-lookup"><span data-stu-id="e7881-128">This version of the NetX Duo SNMP Agent has the following constraints:</span></span>

1. <span data-ttu-id="e7881-129">En SNMP-agent per NetX IP-instans</span><span class="sxs-lookup"><span data-stu-id="e7881-129">One SNMP Agent per NetX IP Instance</span></span>
2. <span data-ttu-id="e7881-130">Inget stöd för RMON</span><span class="sxs-lookup"><span data-stu-id="e7881-130">No support for RMON</span></span>
3. <span data-ttu-id="e7881-131">SNMP v3-informerar meddelanden stöds inte</span><span class="sxs-lookup"><span data-stu-id="e7881-131">SNMP v3 Inform messages are not supported</span></span>
4. <span data-ttu-id="e7881-132">TÄCKANDE och NSAP-datatyper stöds inte</span><span class="sxs-lookup"><span data-stu-id="e7881-132">OPAQUE and NSAP data types are not supported</span></span>
5. <span data-ttu-id="e7881-133">IPv6-adresser definieras som oktett-strängar och format kontroll lämnas till programmet.</span><span class="sxs-lookup"><span data-stu-id="e7881-133">IPv6 addresses are defined as octet strings, and format checking is left to the application.</span></span>

## <a name="snmp-object-names"></a><span data-ttu-id="e7881-134">Namn på SNMP-objekt</span><span class="sxs-lookup"><span data-stu-id="e7881-134">SNMP Object Names</span></span>

<span data-ttu-id="e7881-135">SNMP-protokollet är utformat för att hantera enheter på Internet.</span><span class="sxs-lookup"><span data-stu-id="e7881-135">The SNMP protocol is designed to manage devices on the internet.</span></span> <span data-ttu-id="e7881-136">För att åstadkomma detta har varje SNMP-hanterad enhet en uppsättning objekt som definieras av strukturen för hanterings information (SMI) enligt definitionen i RFC 1155.</span><span class="sxs-lookup"><span data-stu-id="e7881-136">To accomplish this, each SNMP managed device has a set of objects that are defined by the Structure of Management Information (SMI) as defined by RFC 1155.</span></span> <span data-ttu-id="e7881-137">Strukturen är en hierarkisk träd struktur typ som ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="e7881-137">The structure is a hierarchical tree type of structure that looks like the following:</span></span>

![Diagram över hanterings informationens struktur.](media/image3.png)

<span data-ttu-id="e7881-139">Varje nod i trädet är ett objekt.</span><span class="sxs-lookup"><span data-stu-id="e7881-139">Each node in the tree is an object.</span></span> <span data-ttu-id="e7881-140">"DoD"-objektet i trädet identifieras av Notations-1.3.6, medan "Internet"-objektet i trädet identifieras av notation-1.3.6.1.</span><span class="sxs-lookup"><span data-stu-id="e7881-140">The “dod” object in the tree is identified by the notation 1.3.6, while the “internet” object in the tree is identified by the notation 1.3.6.1.</span></span> <span data-ttu-id="e7881-141">Alla namn på SNMP-objekt börjar med notationen 1.3.6.</span><span class="sxs-lookup"><span data-stu-id="e7881-141">All SNMP object names begin with the notation 1.3.6.</span></span>

<span data-ttu-id="e7881-142">En SNMP-hanterare använder den här objekt notationen för att ange vilket objekt i enheten som den vill hämta eller ange.</span><span class="sxs-lookup"><span data-stu-id="e7881-142">An SNMP Manager uses this object notation to specify what object in the device it wishes to get or set.</span></span> <span data-ttu-id="e7881-143">NetX Duo SNMP-agenten tolkar sådana Manager-begäranden och tillhandahåller mekanismer för att utföra den begärda åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e7881-143">The NetX Duo SNMP Agent interprets such manager requests and provides mechanisms for the application to perform the requested operation.</span></span>

## <a name="snmp-manager-requests"></a><span data-ttu-id="e7881-144">SNMP Manager-begäranden</span><span class="sxs-lookup"><span data-stu-id="e7881-144">SNMP Manager Requests</span></span>

<span data-ttu-id="e7881-145">SNMP har en enkel mekanism för att hantera enheter.</span><span class="sxs-lookup"><span data-stu-id="e7881-145">The SNMP has a simple mechanism for managing devices.</span></span> <span data-ttu-id="e7881-146">Det finns en uppsättning vanliga SNMP-kommandon som utfärdas av SNMP-hanteraren till SNMP-enheten på *port 161*.</span><span class="sxs-lookup"><span data-stu-id="e7881-146">There is a set of standard SNMP commands that are issued by the SNMP Manager to the SNMP device on *port 161*.</span></span> <span data-ttu-id="e7881-147">Nedan visas några av de grundläggande SNMP Manager-kommandona:</span><span class="sxs-lookup"><span data-stu-id="e7881-147">The following shows some of the basic SNMP Manager commands:</span></span>

| <span data-ttu-id="e7881-148">SNMP-kommando</span><span class="sxs-lookup"><span data-stu-id="e7881-148">SNMP Command</span></span> | <span data-ttu-id="e7881-149">Innebörd</span><span class="sxs-lookup"><span data-stu-id="e7881-149">Meaning</span></span>                                                        |
|--------------|----------------------------------------------------------------|
| <span data-ttu-id="e7881-150">GET</span><span class="sxs-lookup"><span data-stu-id="e7881-150">GET</span></span>          | <span data-ttu-id="e7881-151">*Hämta det angivna objektet*</span><span class="sxs-lookup"><span data-stu-id="e7881-151">*Get the specified object*</span></span>                                       |
| <span data-ttu-id="e7881-152">GETNEXT</span><span class="sxs-lookup"><span data-stu-id="e7881-152">GETNEXT</span></span>      | <span data-ttu-id="e7881-153">*Hämta nästa logiska objekt efter angivet objekt-ID*</span><span class="sxs-lookup"><span data-stu-id="e7881-153">*Get the next logical object after the specified object ID*</span></span>      |
| <span data-ttu-id="e7881-154">GETBULK</span><span class="sxs-lookup"><span data-stu-id="e7881-154">GETBULK</span></span>      | <span data-ttu-id="e7881-155">*Hämta flera logiska objekt efter angivet objekt-ID*</span><span class="sxs-lookup"><span data-stu-id="e7881-155">*Get the multiple logical objects after the specified object ID*</span></span> |
| <span data-ttu-id="e7881-156">SET</span><span class="sxs-lookup"><span data-stu-id="e7881-156">SET</span></span>          | <span data-ttu-id="e7881-157">*Ange det angivna objektet*</span><span class="sxs-lookup"><span data-stu-id="e7881-157">*Set the specified object*</span></span>                                       |

<span data-ttu-id="e7881-158">De här kommandona är kodade i formatet för abstrakt syntax notation One (ASN. 1) och finns i nytto lasten för UDP-paketet som skickas av SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="e7881-158">These commands are encoded in the Abstract Syntax Notation One (ASN.1) format and reside in the payload of the UDP packet sent by the SNMP Manager.</span></span> <span data-ttu-id="e7881-159">NetX Duo SNMP-agenten bearbetar begäran och anropar sedan motsvarande hanterings rutin som anges i ***nx_snmp_agent_create*** -anropet.</span><span class="sxs-lookup"><span data-stu-id="e7881-159">The NetX Duo SNMP Agent processes the request and then calls the corresponding handling routine specified in the ***nx_snmp_agent_create*** call.</span></span>

## <a name="netx-duo-snmp-agent-traps"></a><span data-ttu-id="e7881-160">NetX Duo SNMP-agentens traps</span><span class="sxs-lookup"><span data-stu-id="e7881-160">NetX Duo SNMP Agent Traps</span></span>

<span data-ttu-id="e7881-161">NetX Duo SNMP-agenten ger möjlighet att även varna en SNMP-hanterare av händelser asynkront.</span><span class="sxs-lookup"><span data-stu-id="e7881-161">The NetX Duo SNMP Agent provides the ability to also alert an SNMP Manager of events asynchronously.</span></span> <span data-ttu-id="e7881-162">Detta görs via ett SNMP-trap-kommando.</span><span class="sxs-lookup"><span data-stu-id="e7881-162">This is done via an SNMP trap command.</span></span> <span data-ttu-id="e7881-163">Det finns ett unikt API för varje version av SNMP för att skicka traps till en SNMP-hanterare.</span><span class="sxs-lookup"><span data-stu-id="e7881-163">There is a unique API for each version of SNMP for sending traps to an SNMP Manager.</span></span> <span data-ttu-id="e7881-164">Som standard skickas traps till SNMP-hanteraren på port 162.</span><span class="sxs-lookup"><span data-stu-id="e7881-164">By default, the traps are sent to the SNMP Manager on port 162.</span></span>

<span data-ttu-id="e7881-165">NetX Duo SNMP-agenten innehåller separata säkerhets nycklar för meddelanden om SNMPv3-trap.</span><span class="sxs-lookup"><span data-stu-id="e7881-165">The NetX Duo SNMP Agent provides separate security keys for SNMPv3 trap messages.</span></span> <span data-ttu-id="e7881-166">För att göra det måste SNMP-programmet skapa en separat uppsättning nycklar från de som tillämpas på svar till Manager-begäranden.</span><span class="sxs-lookup"><span data-stu-id="e7881-166">To do so, the SNMP application must create a separate set of keys from those applied to responses to Manager requests.</span></span> <span data-ttu-id="e7881-167">Med trap-säkerhet kan SNMP-agenten använda samma eller olika lösen ord för autentisering och sekretess.</span><span class="sxs-lookup"><span data-stu-id="e7881-167">Trap security enables the SNMP Agent to use the same or different passwords for authentication and privacy.</span></span> <span data-ttu-id="e7881-168">Mer information om hur du skapar säkerhets nycklar finns i **netx Duo SNMP-autentisering och kryptering** i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="e7881-168">For more information on creating security keys, see **NetX Duo SNMP Authentication and Encryption** in the next section.</span></span>

<span data-ttu-id="e7881-169">En lista med variabler för standard-SNMP-trap räknas upp överst i *nxd_snmp. h:*</span><span class="sxs-lookup"><span data-stu-id="e7881-169">A list of standard SNMP trap variables is enumerated at the top of *nxd_snmp.h:*</span></span>

| <span data-ttu-id="e7881-170">Variabler</span><span class="sxs-lookup"><span data-stu-id="e7881-170">Variables</span></span>                                 | <span data-ttu-id="e7881-171">Värde</span><span class="sxs-lookup"><span data-stu-id="e7881-171">Value</span></span>  |
|-------------------------------------------|---|
| <span data-ttu-id="e7881-172">#define NX_SNMP_TRAP_COLDSTART</span><span class="sxs-lookup"><span data-stu-id="e7881-172">#define NX_SNMP_TRAP_COLDSTART</span></span>            | <span data-ttu-id="e7881-173">0</span><span class="sxs-lookup"><span data-stu-id="e7881-173">0</span></span> |
| <span data-ttu-id="e7881-174">#define NX_SNMP_TRAP_WARMSTART</span><span class="sxs-lookup"><span data-stu-id="e7881-174">#define NX_SNMP_TRAP_WARMSTART</span></span>            | <span data-ttu-id="e7881-175">1</span><span class="sxs-lookup"><span data-stu-id="e7881-175">1</span></span> |
| <span data-ttu-id="e7881-176">#define NX_SNMP_TRAP_LINKDOWN</span><span class="sxs-lookup"><span data-stu-id="e7881-176">#define NX_SNMP_TRAP_LINKDOWN</span></span>             | <span data-ttu-id="e7881-177">2</span><span class="sxs-lookup"><span data-stu-id="e7881-177">2</span></span> |
| <span data-ttu-id="e7881-178">#define NX_SNMP_TRAP_LINKUP</span><span class="sxs-lookup"><span data-stu-id="e7881-178">#define NX_SNMP_TRAP_LINKUP</span></span>               | <span data-ttu-id="e7881-179">3</span><span class="sxs-lookup"><span data-stu-id="e7881-179">3</span></span> |
| <span data-ttu-id="e7881-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span><span class="sxs-lookup"><span data-stu-id="e7881-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span></span> | <span data-ttu-id="e7881-181">4</span><span class="sxs-lookup"><span data-stu-id="e7881-181">4</span></span> |
| <span data-ttu-id="e7881-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span><span class="sxs-lookup"><span data-stu-id="e7881-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span></span>      | <span data-ttu-id="e7881-183">5</span><span class="sxs-lookup"><span data-stu-id="e7881-183">5</span></span> |
| <span data-ttu-id="e7881-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span><span class="sxs-lookup"><span data-stu-id="e7881-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span></span>   | <span data-ttu-id="e7881-185">6</span><span class="sxs-lookup"><span data-stu-id="e7881-185">6</span></span> |

<span data-ttu-id="e7881-186">Om du vill inkludera dessa variabler i trap-meddelandet, trap_type indataargumentet i *nx_snmp_agent_trapv2_send* (SNMPv2) eller *nx_snmp_agent_trapv3_send* (SNMPv3) anges till det uppräknade värdet för dessa variabler.</span><span class="sxs-lookup"><span data-stu-id="e7881-186">To include these variables in the trap message, the trap_type input argument in *nx_snmp_agent_trapv2_send* (SNMPv2) or *nx_snmp_agent_trapv3_send* (SNMPv3) is set to the enumerated value of these variables.</span></span> <span data-ttu-id="e7881-187">Ett exempel visas nedan för SNMPv2 för att meddela SNMP-hanteraren om en kall start händelse:</span><span class="sxs-lookup"><span data-stu-id="e7881-187">An example is shown below for SNMPv2 to notify the SNMP Manager of a cold start event:</span></span>

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

<span data-ttu-id="e7881-188">Om du vill inkludera tillverkarspecifika variabler i trap-meddelandet anges argumentet trap_type indataargumentet till NX_SNMP_TRAP_CUSTOM och indataargumentet för trap-listan innehåller de tillverkarspecifika data.</span><span class="sxs-lookup"><span data-stu-id="e7881-188">To include proprietary variables in the trap message, the trap_type input argument is set to NX_SNMP_TRAP_CUSTOM and the trap list input argument contains the proprietary data.</span></span> <span data-ttu-id="e7881-189">Observera att trap-meddelandet kommer att innehålla som system tid (1.3.6.1.6.3.1.1.4.1.0).</span><span class="sxs-lookup"><span data-stu-id="e7881-189">Note that the trap message will contain as the system up time (1.3.6.1.6.3.1.1.4.1.0).</span></span> <span data-ttu-id="e7881-190">Ett exempel visas nedan för SNMPv2:</span><span class="sxs-lookup"><span data-stu-id="e7881-190">An example is shown below for SNMPv2:</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a><span data-ttu-id="e7881-191">NetX Duo SNMP-autentisering och kryptering</span><span class="sxs-lookup"><span data-stu-id="e7881-191">NetX Duo SNMP Authentication and Encryption</span></span>

<span data-ttu-id="e7881-192">Det finns två varianter-autentisering, nämligen *Basic* och *Digest*.</span><span class="sxs-lookup"><span data-stu-id="e7881-192">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="e7881-193">Grundläggande autentisering motsvarar en enkel autentisering med oformaterad text- *username* i många protokoll.</span><span class="sxs-lookup"><span data-stu-id="e7881-193">Basic authentication is equivalent to a simple plain text *username* authentication found in many protocols.</span></span> <span data-ttu-id="e7881-194">I grundläggande SNMP-autentisering verifierar användaren bara att det angivna användar namnet är giltigt för att utföra SNMP-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="e7881-194">In SNMP basic authentication, the user simply verifies that the supplied username is valid for performing SNMP operations.</span></span> <span data-ttu-id="e7881-195">Grundläggande autentisering är det enda alternativet för SNMP version 1 och 2.</span><span class="sxs-lookup"><span data-stu-id="e7881-195">Basic authentication is the only option for SNMP versions 1 and 2.</span></span>

<span data-ttu-id="e7881-196">Den största nack delen med grundläggande autentisering är att användar namnet överförs som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="e7881-196">The main disadvantage of basic authentication is the username is transmitted in plain text.</span></span> <span data-ttu-id="e7881-197">SNMPv3 Digest-autentiseringen åtgärdar det här problemet genom att aldrig överföra användar namnet som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="e7881-197">The SNMPv3 digest authentication addresses this problem by never transmitting the username in plain text.</span></span> <span data-ttu-id="e7881-198">I stället används en algoritm för att härleda en 96-bitars sammandrag från användar namnet, kontext motorn och annan information.</span><span class="sxs-lookup"><span data-stu-id="e7881-198">Instead, an algorithm is used to derive a 96-bit ‘digest’ from the username, context engine, and other information.</span></span> <span data-ttu-id="e7881-199">NetX Duo SNMP-agenten har stöd för både MD5-och SHA-algoritmer.</span><span class="sxs-lookup"><span data-stu-id="e7881-199">The NetX Duo SNMP Agent supports both MD5 and SHA digest algorithms.</span></span>

<span data-ttu-id="e7881-200">Om du vill aktivera autentisering måste SNMP-agenten ange sitt kontext motor-ID med hjälp av *nx_snmp_agent_context_engine_set* tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e7881-200">To enable authentication, the SNMP Agent must set its Context Engine ID using the *nx_snmp_agent_context_engine_set* service.</span></span> <span data-ttu-id="e7881-201">Kontext motorns ID används i skapandet av autentiseringsnyckel.</span><span class="sxs-lookup"><span data-stu-id="e7881-201">The Context Engine ID is used in the creation of the authentication key.</span></span>

<span data-ttu-id="e7881-202">Kryptering av SNMPv3-data är tillgängligt med DES-algoritmen.</span><span class="sxs-lookup"><span data-stu-id="e7881-202">Encryption of SNMPv3 data is available using the DES algorithm.</span></span> <span data-ttu-id="e7881-203">Kryptering kräver att autentisering är aktiverat (en kan inte kryptera data utan att ange autentiseringsinställningarna).</span><span class="sxs-lookup"><span data-stu-id="e7881-203">Encryption requires that authentication be enabled (one cannot encrypt data without setting the authentication parameters).</span></span>

<span data-ttu-id="e7881-204">Följande API används för att skapa autentiserings-och sekretess nycklar:</span><span class="sxs-lookup"><span data-stu-id="e7881-204">To create authentication and privacy keys, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

<span data-ttu-id="e7881-205">Därefter måste SNMP-agenten konfigureras att använda dessa nycklar.</span><span class="sxs-lookup"><span data-stu-id="e7881-205">Next, the SNMP agent must be configured to use these keys.</span></span> <span data-ttu-id="e7881-206">Följande API används för att registrera en nyckel med SNMP-agenten:</span><span class="sxs-lookup"><span data-stu-id="e7881-206">To register a key with the SNMP agent, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="e7881-207">Du kan skapa separata nycklar för trap-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="e7881-207">Separate keys can be created for trap messages.</span></span> <span data-ttu-id="e7881-208">Följande API är tillgängliga om du vill använda nycklar för trap-meddelanden:</span><span class="sxs-lookup"><span data-stu-id="e7881-208">To apply keys for trap messages the following API are available:</span></span>

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="e7881-209">Om du vill inaktivera autentisering eller kryptering för svarsmeddelanden och skicka traps, använder du dessa tjänster med indatamängden för nyckel pekare till NULL.</span><span class="sxs-lookup"><span data-stu-id="e7881-209">To disable authentication or encryption for response messages and sending traps, use these services with the key pointer input set to NULL.</span></span>

## <a name="netx-duo-snmp-community-strings"></a><span data-ttu-id="e7881-210">NetX Duo SNMP community-strängar</span><span class="sxs-lookup"><span data-stu-id="e7881-210">NetX Duo SNMP Community Strings</span></span>

<span data-ttu-id="e7881-211">NetX Duo SNMP-agenten stöder både offentliga och privata grupp strängar.</span><span class="sxs-lookup"><span data-stu-id="e7881-211">The NetX Duo SNMP Agent supports both public and private community strings.</span></span> <span data-ttu-id="e7881-212">Den offentliga strängen anges med tjänsten *nx_snmp_agent _public_string_set* .</span><span class="sxs-lookup"><span data-stu-id="e7881-212">The public string is set with the *nx_snmp_agent _public_string_set* service.</span></span> <span data-ttu-id="e7881-213">Den privata strängen för NetX Duo SNMP-agenten anges med hjälp av tjänsten *nx_snmp_agent_private_string_set* .</span><span class="sxs-lookup"><span data-stu-id="e7881-213">The NetX Duo SNMP Agent private string is set using the *nx_snmp_agent_private_string_set* service.</span></span>

## <a name="netx-duo-snmp-username-callback"></a><span data-ttu-id="e7881-214">NetX Duo SNMP username-motanrop</span><span class="sxs-lookup"><span data-stu-id="e7881-214">NetX Duo SNMP Username Callback</span></span>

<span data-ttu-id="e7881-215">NetX Duo SNMP agent-paketet gör att programmet kan ange (via ***nx_snmp_agent_create*** -anrop) ett användar namn för motringning som anropas i början av hantering av varje SNMP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="e7881-215">The NetX Duo SNMP Agent package allows the application to specify (via the ***nx_snmp_agent_create*** call) a username callback  that is called at the beginning of handling each SNMP Client request.</span></span>

<span data-ttu-id="e7881-216">Återanrops rutinen ger NetX Duo SNMP-agenten med användar namnet.</span><span class="sxs-lookup"><span data-stu-id="e7881-216">The callback routine provides the NetX Duo SNMP Agent with the username.</span></span> <span data-ttu-id="e7881-217">Om det angivna användar namnet är giltigt eller om ingen användar namns kontroll krävs för att svara på begäran, ska återanropet av användar namnet returnera värdet för **NX_SUCCESS**.</span><span class="sxs-lookup"><span data-stu-id="e7881-217">If the supplied username is valid or if no username check is necessary for the responding to the request, the username callback should return the value of **NX_SUCCESS**.</span></span> <span data-ttu-id="e7881-218">Annars bör rutinen returnera **NX_SNMP_ERROR** för att indikera att det angivna användar namnet är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="e7881-218">Otherwise, the routine should return **NX_SNMP_ERROR** to indicate the specified username is invalid.</span></span>

<span data-ttu-id="e7881-219">Formatet på rutinen för motringning av program användar namn definieras nedan:</span><span class="sxs-lookup"><span data-stu-id="e7881-219">The format of the application username callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

<span data-ttu-id="e7881-220">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e7881-220">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e7881-221">Parameter</span><span class="sxs-lookup"><span data-stu-id="e7881-221">Parameter</span></span> | <span data-ttu-id="e7881-222">Innebörd</span><span class="sxs-lookup"><span data-stu-id="e7881-222">Meaning</span></span>                                              |
|-----------|------------------------------------------------------|
| <span data-ttu-id="e7881-223">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e7881-223">*agent_ptr*</span></span> | <span data-ttu-id="e7881-224">Pekare för att anropa SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="e7881-224">Pointer to calling SNMP agent</span></span>                        |
| <span data-ttu-id="e7881-225">användarnamn</span><span class="sxs-lookup"><span data-stu-id="e7881-225">username</span></span>  | <span data-ttu-id="e7881-226">Mål för pekaren till det begärda användar namnet</span><span class="sxs-lookup"><span data-stu-id="e7881-226">Destination for the pointer to the required username</span></span> |

<span data-ttu-id="e7881-227">För SNMPv1-och SNMPv2/v2C-sessioner ska programmet undersöka grupp strängen i en inkommande SNMP-begäran för att avgöra om SNMP-begäran har en giltig grupp sträng.</span><span class="sxs-lookup"><span data-stu-id="e7881-227">For SNMPv1 and SNMPv2/v2C sessions, the application will want to examine the community string on an incoming SNMP request to determine if the SNMP request has a valid community string.</span></span> <span data-ttu-id="e7881-228">Det finns flera tjänster för SNMP-programmet att göra detta.</span><span class="sxs-lookup"><span data-stu-id="e7881-228">There are several services for the SNMP application to do this.</span></span>

<span data-ttu-id="e7881-229">SNMP-programmet kan fråga om den aktuella SNMP Manager-begäran är GET (t. ex. GET, GETNEXT eller GETBULK) eller ange typ av begäran som använder den här tjänsten:</span><span class="sxs-lookup"><span data-stu-id="e7881-229">The SNMP application can inquire if the current SNMP Manager request is a GET (e.g. GET, GETNEXT, or GETBULK) or SET type of request using this service:</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

<span data-ttu-id="e7881-230">Om begäran är en GET-typ, vill programmet jämföra ingångs grupp strängen med SNMP-agentens offentliga sträng:</span><span class="sxs-lookup"><span data-stu-id="e7881-230">If the request is a GET type, the application will want to compare the input community string to the SNMP Agent’s public string:</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

<span data-ttu-id="e7881-231">Om begäran är en UPPSÄTTNINGs typ vill programmet jämföra ingångs gruppens sträng till SNMP-agentens privata sträng:</span><span class="sxs-lookup"><span data-stu-id="e7881-231">Similarly if the request is a SET type, the application will want to compare the input community string to the SNMP Agent’s private string:</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

<span data-ttu-id="e7881-232">Värdena för is_public och is_private anger om gruppens ingångs sträng är en giltig offentlig eller privat grupp sträng.</span><span class="sxs-lookup"><span data-stu-id="e7881-232">The is_public and is_private return values indicate respectively if the input community string is a valid public or private community string.</span></span>

<span data-ttu-id="e7881-233">Returvärdet för återanrops rutinen för användar namn anger om användar namnet är giltigt.</span><span class="sxs-lookup"><span data-stu-id="e7881-233">The return value of the username callback routine indicates if the username is valid.</span></span> <span data-ttu-id="e7881-234">Värdet **NX_SUCCESS** returneras om användar namnet är giltigt eller **NX_SNMP_ERROR** om användar namnet är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="e7881-234">The value **NX_SUCCESS** is returned if the username is valid, or **NX_SNMP_ERROR** if the username is invalid.</span></span>

## <a name="netx-duo-snmp-agent-get-callback"></a><span data-ttu-id="e7881-235">NetX Duo SNMP-agent Hämta motringning</span><span class="sxs-lookup"><span data-stu-id="e7881-235">NetX Duo SNMP Agent GET Callback</span></span>

<span data-ttu-id="e7881-236">Programmet måste ange en callback-rutin för att hantera GET-objekt-begär Anden från SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="e7881-236">The application must set a callback routine for handling GET object requests from the SNMP Manager.</span></span> <span data-ttu-id="e7881-237">Återanropet hämtar värdet för det objekt som anges i begäran.</span><span class="sxs-lookup"><span data-stu-id="e7881-237">The callback retrieves the value of the object specified in the request.</span></span>

<span data-ttu-id="e7881-238">Rutinen för att hämta återanrops förfrågan anges nedan:</span><span class="sxs-lookup"><span data-stu-id="e7881-238">The application GET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="e7881-239">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e7881-239">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e7881-240">Parameter</span><span class="sxs-lookup"><span data-stu-id="e7881-240">Parameter</span></span>        | <span data-ttu-id="e7881-241">Innebörd</span><span class="sxs-lookup"><span data-stu-id="e7881-241">Meaning</span></span> |
|------------------|----------------------------------|
| <span data-ttu-id="e7881-242">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e7881-242">*agent_ptr*</span></span>        | <span data-ttu-id="e7881-243">Pekare för att anropa SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="e7881-243">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="e7881-244">object_requested</span><span class="sxs-lookup"><span data-stu-id="e7881-244">object_requested</span></span> | <span data-ttu-id="e7881-245">ASCII-sträng som representerar det objekt-ID som åtgärden GET är för.</span><span class="sxs-lookup"><span data-stu-id="e7881-245">ASCII string representing the object ID the GET operation is for.</span></span> |
| <span data-ttu-id="e7881-246">object_data</span><span class="sxs-lookup"><span data-stu-id="e7881-246">object_data</span></span>      | <span data-ttu-id="e7881-247">Data struktur som ska innehålla värdet som hämtas av återanropet.</span><span class="sxs-lookup"><span data-stu-id="e7881-247">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="e7881-248">Detta kan anges med en serie med NetX Duo SNMP API: er som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="e7881-248">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

> [!NOTE]
> <span data-ttu-id="e7881-249">*För oktett-strängar måste objektet tilldelas längden så att den interna funktionen vet hur lång tid det tar eftersom motringningen inte har något längd argument:*</span><span class="sxs-lookup"><span data-stu-id="e7881-249">*For octet strings, the object must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:*</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="e7881-250">Eftersom data typen inte är känd för att hämta motringning, behöver du inte kontrol lera data typen.</span><span class="sxs-lookup"><span data-stu-id="e7881-250">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="e7881-251">Längden får inte påverka numeriska typer eller strängar som är null-avgränsade.</span><span class="sxs-lookup"><span data-stu-id="e7881-251">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="e7881-252">Anropa sedan den interna funktionen:</span><span class="sxs-lookup"><span data-stu-id="e7881-252">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="e7881-253">Om funktionen motringning inte kan hitta det begärda objektet, ska **NX_SNMP_ERROR_NOSUCHNAME** fel koden returneras.</span><span class="sxs-lookup"><span data-stu-id="e7881-253">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="e7881-254">Om något annat fel upptäcks, ska **NX_SNMP_ERROR** returneras.</span><span class="sxs-lookup"><span data-stu-id="e7881-254">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-getnext-callback"></a><span data-ttu-id="e7881-255">NetX Duo SNMP-agent GETNEXT motringning</span><span class="sxs-lookup"><span data-stu-id="e7881-255">NetX Duo SNMP Agent GETNEXT Callback</span></span>

<span data-ttu-id="e7881-256">Programmet måste också ange callback-rutinen för GETNEXT-objekt begär Anden från SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="e7881-256">The application must also set the callback routine for GETNEXT object requests from the SNMP Manager.</span></span> <span data-ttu-id="e7881-257">GETNEXT-återanropet hämtar värdet för nästa objekt som anges av begäran.</span><span class="sxs-lookup"><span data-stu-id="e7881-257">The GETNEXT callback retrieves the value of the next object specified by the request.</span></span>

<span data-ttu-id="e7881-258">Rutinen för begäran om program GETNEXT anges nedan:</span><span class="sxs-lookup"><span data-stu-id="e7881-258">The application GETNEXT request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="e7881-259">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e7881-259">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e7881-260">Parameter</span><span class="sxs-lookup"><span data-stu-id="e7881-260">Parameter</span></span>        | <span data-ttu-id="e7881-261">Innebörd</span><span class="sxs-lookup"><span data-stu-id="e7881-261">Meaning</span></span> |
|------------------|-------------------------------------------|
| <span data-ttu-id="e7881-262">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e7881-262">*agent_ptr*</span></span>        | <span data-ttu-id="e7881-263">Pekare för att anropa SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="e7881-263">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="e7881-264">object_requested</span><span class="sxs-lookup"><span data-stu-id="e7881-264">object_requested</span></span> | <span data-ttu-id="e7881-265">ASCII-sträng som representerar det objekt-ID som GETNEXT-åtgärden avser.</span><span class="sxs-lookup"><span data-stu-id="e7881-265">ASCII string representing the object ID the GETNEXT operation is for.</span></span> |
| <span data-ttu-id="e7881-266">object_data</span><span class="sxs-lookup"><span data-stu-id="e7881-266">object_data</span></span>      | <span data-ttu-id="e7881-267">Data struktur som ska innehålla värdet som hämtas av återanropet.</span><span class="sxs-lookup"><span data-stu-id="e7881-267">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="e7881-268">Detta kan anges med en serie med NetX Duo SNMP API: er som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="e7881-268">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="e7881-269">Samma som sant för GET-återanrop måste objekt med oktett-strängar tilldelas längden så att den interna funktionen vet hur lång tid det tar eftersom motringningen inte har ett längd argument:</span><span class="sxs-lookup"><span data-stu-id="e7881-269">Same as is true for GET callbacks, objects with octet string data must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="e7881-270">Eftersom data typen inte är känd för att hämta motringning, behöver du inte kontrol lera data typen.</span><span class="sxs-lookup"><span data-stu-id="e7881-270">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="e7881-271">Längden får inte påverka numeriska typer eller strängar som är null-avgränsade.</span><span class="sxs-lookup"><span data-stu-id="e7881-271">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="e7881-272">Anropa sedan den interna funktionen:</span><span class="sxs-lookup"><span data-stu-id="e7881-272">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="e7881-273">Om funktionen motringning inte kan hitta det begärda objektet, ska **NX_SNMP_ERROR_NOSUCHNAME** fel koden returneras.</span><span class="sxs-lookup"><span data-stu-id="e7881-273">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="e7881-274">Om något annat fel upptäcks, ska **NX_SNMP_ERROR** returneras.</span><span class="sxs-lookup"><span data-stu-id="e7881-274">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-set-callback"></a><span data-ttu-id="e7881-275">NetX Duo SNMP-agent ange motringning</span><span class="sxs-lookup"><span data-stu-id="e7881-275">NetX Duo SNMP Agent SET Callback</span></span>

<span data-ttu-id="e7881-276">Programmet ska ange callback-rutinen för hantering av objekt begär Anden från SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="e7881-276">The application should set the callback routine for handling SET object requests from the SNMP Manager.</span></span> <span data-ttu-id="e7881-277">SET motringning anger värdet för det objekt som anges av begäran.</span><span class="sxs-lookup"><span data-stu-id="e7881-277">The SET callback sets the value of the object specified by the request.</span></span>

<span data-ttu-id="e7881-278">Rutinen för motringning av program uppsättning definieras nedan:</span><span class="sxs-lookup"><span data-stu-id="e7881-278">The application SET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="e7881-279">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e7881-279">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e7881-280">Parameter</span><span class="sxs-lookup"><span data-stu-id="e7881-280">Parameter</span></span>        | <span data-ttu-id="e7881-281">Innebörd</span><span class="sxs-lookup"><span data-stu-id="e7881-281">Meaning</span></span> |
|------------------|-------- |
| <span data-ttu-id="e7881-282">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e7881-282">*agent_ptr*</span></span>      | <span data-ttu-id="e7881-283">Pekare för att anropa SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="e7881-283">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="e7881-284">object_requested</span><span class="sxs-lookup"><span data-stu-id="e7881-284">object_requested</span></span> | <span data-ttu-id="e7881-285">ASCII-sträng som representerar det objekt-ID som åtgärden ställs in för.</span><span class="sxs-lookup"><span data-stu-id="e7881-285">ASCII string representing the object ID the SET operation is for.</span></span> |
| <span data-ttu-id="e7881-286">object_data</span><span class="sxs-lookup"><span data-stu-id="e7881-286">object_data</span></span>      | <span data-ttu-id="e7881-287">Data struktur som innehåller det nya värdet för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="e7881-287">Data structure that contains the new value for the specified object.</span></span> <span data-ttu-id="e7881-288">Den faktiska åtgärden kan utföras med hjälp av NetX Duo SNMP API: erna som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="e7881-288">The actual operation can be done using the NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="e7881-289">Observera att om du skapar en oktett-sträng ska MIB-tabellen uppdatera MIB-tabellen med data längden eftersom SNMP-agenten har parsat data och känner till typ och längd:</span><span class="sxs-lookup"><span data-stu-id="e7881-289">Note that for octet strings, the SET callback should update the MIB table with the length of the data since the SNMP Agent has parsed the data and knows the type and length:</span></span>

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

<span data-ttu-id="e7881-290">Om funktionen motringning inte kan hitta det begärda objektet, ska **NX_SNMP_ERROR_NOSUCHNAME** fel koden returneras.</span><span class="sxs-lookup"><span data-stu-id="e7881-290">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span>

<span data-ttu-id="e7881-291">Om NetX Duo SNMP-värden har skapat privata grupp strängar och SNMP-avsändaren för SET-begäran inte har den matchande privata strängen, kan den returnera ett **NX_SNMP_ERROR_NOACCESS** fel.</span><span class="sxs-lookup"><span data-stu-id="e7881-291">If the NetX Duo SNMP host has created private community strings, and the SNMP sender of the SET request does not have the matching private string, it may return an **NX_SNMP_ERROR_NOACCESS** error.</span></span> <span data-ttu-id="e7881-292">Om något annat fel upptäcks, ska **NX_SNMP_ERROR** returneras.</span><span class="sxs-lookup"><span data-stu-id="e7881-292">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

> [!NOTE]
> <span data-ttu-id="e7881-293">*Även om NetX Duo SNMP-agenten tillhandahåller en SNMP MIB-databas med distributionen, är det främst för testning och utveckling. Utvecklare kräver förmodligen en patentskyddad MIB-databas för ett professionellt SNMP-program.*</span><span class="sxs-lookup"><span data-stu-id="e7881-293">*Although NetX Duo SNMP Agent supplies an SNMP MIB database with the distribution, it is primarily for testing and development purposes. The developer will likely require a proprietary MIB database for a professional SNMP application.*</span></span>

## <a name="changing-snmp-version-at-run-time"></a><span data-ttu-id="e7881-294">Ändra SNMP-version vid körning</span><span class="sxs-lookup"><span data-stu-id="e7881-294">Changing SNMP Version at Run Time</span></span>

<span data-ttu-id="e7881-295">SNMP-agentens värd kan ändra SNMP-version för var och en av de tre versionerna vid körning med hjälp av tjänsten *nx_snmp_agent_set_version* .</span><span class="sxs-lookup"><span data-stu-id="e7881-295">The SNMP Agent host can change SNMP version for each of the three versions at run time using the *nx_snmp_agent_set_version* service.</span></span> <span data-ttu-id="e7881-296">SNMP-agenten aktive ras som standard för alla tre versioner när SNMP-agenten skapas i *nx_snmp_agent_create*.</span><span class="sxs-lookup"><span data-stu-id="e7881-296">The SNMP Agent is by default enabled for all three versions when the SNMP Agent is created in *nx_snmp_agent_create*.</span></span> <span data-ttu-id="e7881-297">Programmet kan dock begränsas till en delmängd av alla versioner.</span><span class="sxs-lookup"><span data-stu-id="e7881-297">However, the application can limit that to a subset of all versions.</span></span>

> [!NOTE]
> <span data-ttu-id="e7881-298">*Om konfigurations alternativen NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 och/eller NX_SNMP_DISABLE_V3 har definierats, har den här funktionen ingen inverkan som gör det möjligt att använda de versioner som påverkas.*</span><span class="sxs-lookup"><span data-stu-id="e7881-298">*If the configuration options NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 and/or NX_SNMP_DISABLE_V3 are defined, this function will have no effect enabling the effected versions.*</span></span>

<span data-ttu-id="e7881-299">SNMP-agenten kan hämta SNMP-versionen av det senaste SNMP-paketet som togs emot med hjälp av tjänsten *nx_snmp_agent_get_current_version* .</span><span class="sxs-lookup"><span data-stu-id="e7881-299">The SNMP Agent can retrieve the SNMP version of the latest SNMP packet received using the *nx_snmp_agent_get_current_version* service.</span></span>

## <a name="snmpv3-discovery"></a><span data-ttu-id="e7881-300">SNMPv3-identifiering</span><span class="sxs-lookup"><span data-stu-id="e7881-300">SNMPv3 Discovery</span></span>

<span data-ttu-id="e7881-301">SNMP-agenten, om den är aktive rad för SNMPv3, kommer att svara på identifierings begär Anden från SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="e7881-301">The SNMP Agent, if enabled for SNMPv3, will respond to discovery requests from the SNMP Manager.</span></span> <span data-ttu-id="e7881-302">En sådan begäran innehåller säkerhets parameter data med null-värden för auktoritativt motor-ID, användar namn, start antal och start tid.</span><span class="sxs-lookup"><span data-stu-id="e7881-302">Such a request contains security parameter data with null values for Authoritative Engine ID, user name, boot count and boot time.</span></span> <span data-ttu-id="e7881-303">Autentiseringsinställningarna används inte för IDENTIFIERINGs meddelandet.</span><span class="sxs-lookup"><span data-stu-id="e7881-303">Authentication parameters are not applied to the DISCOVERY message.</span></span> <span data-ttu-id="e7881-304">Variabel bindnings listan i begäran är tom (innehåller noll objekt).</span><span class="sxs-lookup"><span data-stu-id="e7881-304">The variable binding list in the request is empty (contains zero items).</span></span> <span data-ttu-id="e7881-305">SNMP-agenten svarar med noll start tid och antal, och variabel bindnings listan som innehåller 1 objekt, *usmStatsUnknownEngineIDs*, vilket är antalet förfrågningar som tagits emot med ett okänt motor-ID (null).</span><span class="sxs-lookup"><span data-stu-id="e7881-305">The SNMP agent responds with a zero boot time and count, and the variable binding list containing 1 item, *usmStatsUnknownEngineIDs*, which is the count of requests received with an unknown (null) engine ID.</span></span> <span data-ttu-id="e7881-306">På den efterföljande GETNEXT-begäran från webbläsaren/hanteraren fylls start data och säkerhets parametrar bara i om säkerhet är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="e7881-306">On the subsequent GETNEXT request from the Browser/Manager, the boot data and security parameters are filled in only if security is enabled.</span></span> <span data-ttu-id="e7881-307">Om så är fallet skickas även en NotInTime-datauppdatering i PDU.</span><span class="sxs-lookup"><span data-stu-id="e7881-307">If so it will also send a NotInTime data update in the PDU.</span></span> <span data-ttu-id="e7881-308">Säkerhets parametrarna, t. ex. autentisering, visar identiteten för agenten för chefen.</span><span class="sxs-lookup"><span data-stu-id="e7881-308">The security parameters, e.g. authentication prove the identity of the Agent to the Manager.</span></span>

<span data-ttu-id="e7881-309">Mer detaljerad information om SNMPv3-autentisering finns i RFC 3414 "User-based Security Model (USM POLICYEGENSKAPER) för version 3 av Simple Network Management Protocol (SNMPv3)".</span><span class="sxs-lookup"><span data-stu-id="e7881-309">More detailed information on SNMPv3 authentication is available in RFC 3414 “User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)”.</span></span>

## <a name="netx-duo-snmp-rfcs"></a><span data-ttu-id="e7881-310">NetX Duo SNMP-RFC</span><span class="sxs-lookup"><span data-stu-id="e7881-310">NetX Duo SNMP RFCs</span></span>

<span data-ttu-id="e7881-311">NetX Duo SNMP är kompatibelt med RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 och relaterade RFC: er.</span><span class="sxs-lookup"><span data-stu-id="e7881-311">NetX Duo SNMP is compliant with RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 and related RFCs.</span></span>
