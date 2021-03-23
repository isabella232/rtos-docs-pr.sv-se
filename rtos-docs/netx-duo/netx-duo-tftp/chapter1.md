---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo TFTP
description: Trivial File Transfer Protocol (TFTP) är ett Lightweight-protokoll som är utformat för fil överföringar.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825710"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="deea8-103">Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="deea8-103">Chapter 1 - Introduction to Azure RTOS NetX Duo TFTP</span></span> 

<span data-ttu-id="deea8-104">Trivial File Transfer Protocol (TFTP) är ett Lightweight-protokoll som är utformat för fil överföringar.</span><span class="sxs-lookup"><span data-stu-id="deea8-104">The Trivial File Transfer Protocol (TFTP) is a lightweight protocol designed for file transfers.</span></span> <span data-ttu-id="deea8-105">Till skillnad från robusta protokoll utför TFTP inte en omfattande fel kontroll och kan också ha begränsad prestanda eftersom det är ett stopp-och-wait-protokoll.</span><span class="sxs-lookup"><span data-stu-id="deea8-105">Unlike more robust protocols, TFTP does not perform extensive error checking and can also have limited performance because it is a stop-and-wait protocol.</span></span> <span data-ttu-id="deea8-106">När ett TFTP-datapaket har skickats väntar avsändaren tills en bekräftelse skickas tillbaka av mottagaren.</span><span class="sxs-lookup"><span data-stu-id="deea8-106">After a TFTP data packet is sent, the sender waits for an ACK to be returned by the recipient.</span></span> <span data-ttu-id="deea8-107">Även om detta är enkelt begränsar det det övergripande TFTP-dataflödet.</span><span class="sxs-lookup"><span data-stu-id="deea8-107">Although this is simple, it does limit the overall TFTP throughput.</span></span> <span data-ttu-id="deea8-108">Med TFTP-paketet kan värdar använda TFTP-protokollet över IP-nätverk.</span><span class="sxs-lookup"><span data-stu-id="deea8-108">The TFTP package enables hosts to use the TFTP protocol over IP networks.</span></span>

## <a name="tftp-requirements"></a><span data-ttu-id="deea8-109">TFTP-krav</span><span class="sxs-lookup"><span data-stu-id="deea8-109">TFTP Requirements</span></span>

<span data-ttu-id="deea8-110">För att fungera korrekt kräver TFTP-klienter i NetX Duo-paketet att en IP-instans redan har skapats.</span><span class="sxs-lookup"><span data-stu-id="deea8-110">In order to function properly, the TFTP Clients portion of the NetX Duo TFTP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="deea8-111">Dessutom måste UDP vara aktiverat på samma IP-instans.</span><span class="sxs-lookup"><span data-stu-id="deea8-111">In addition, UDP must be enabled on that same IP instance.</span></span> <span data-ttu-id="deea8-112">Klient delen av NetX Duo TFTP-paketet har inga ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="deea8-112">The Client portion of the NetX Duo TFTP package has no further requirements.</span></span>

<span data-ttu-id="deea8-113">TFTP-server delen av NetX Duo TFTP-paketet har flera ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="deea8-113">The TFTP Server portion of the NetX Duo TFTP package has several additional requirements.</span></span> <span data-ttu-id="deea8-114">Först måste du ha fullständig åtkomst till den UDP- *välkända porten 69* för att hantera alla förfrågningar om klient-TFTP.</span><span class="sxs-lookup"><span data-stu-id="deea8-114">First, it requires complete access to the UDP *well known port 69* for handling all client TFTP requests.</span></span> <span data-ttu-id="deea8-115">TFTP-servern är också avsedd att användas med det inbäddade fil systemet FileX.</span><span class="sxs-lookup"><span data-stu-id="deea8-115">The TFTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="deea8-116">Om FileX inte är tillgängligt kan användaren hamna i de delar av FileX som används i sin egen miljö.</span><span class="sxs-lookup"><span data-stu-id="deea8-116">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="deea8-117">Detta beskrivs i senare avsnitt i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="deea8-117">This is discussed in later sections of this guide.</span></span>

## <a name="tftp-file-names"></a><span data-ttu-id="deea8-118">TFTP-filnamn</span><span class="sxs-lookup"><span data-stu-id="deea8-118">TFTP File Names</span></span> 

<span data-ttu-id="deea8-119">TFTP-filnamn ska vara i formatet för mål fil systemet.</span><span class="sxs-lookup"><span data-stu-id="deea8-119">TFTP file names should be in the format of the target file system.</span></span> <span data-ttu-id="deea8-120">De ska vara NULL-terminerade ASCII-strängar, med fullständig Sök vägs information vid behov.</span><span class="sxs-lookup"><span data-stu-id="deea8-120">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="deea8-121">Det finns ingen angiven gräns i storleken på TFTP-filnamn i NetX Duo TFTP-implementeringen.</span><span class="sxs-lookup"><span data-stu-id="deea8-121">There is no specified limit in the size of TFTP file names in the NetX Duo TFTP implementation.</span></span>

## <a name="tftp-messages"></a><span data-ttu-id="deea8-122">TFTP-meddelanden</span><span class="sxs-lookup"><span data-stu-id="deea8-122">TFTP Messages</span></span>

<span data-ttu-id="deea8-123">TFTP har en väldigt enkel mekanism för att öppna, läsa, skriva och stänga filer.</span><span class="sxs-lookup"><span data-stu-id="deea8-123">The TFTP has a very simple mechanism for opening, reading, writing, and closing files.</span></span> <span data-ttu-id="deea8-124">Det finns i princip 2-4 byte i TFTP-huvudet under UDP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="deea8-124">There are basically 2-4 bytes of TFTP header underneath the UDP header.</span></span> <span data-ttu-id="deea8-125">Definitionen av TFTP-filen öppna meddelanden har följande format:</span><span class="sxs-lookup"><span data-stu-id="deea8-125">The definition of the TFTP file open messages has the following format:</span></span>

<span data-ttu-id="deea8-126">**oooof... f0OCTET0**</span><span class="sxs-lookup"><span data-stu-id="deea8-126">**oooof…f0OCTET0**</span></span>

<span data-ttu-id="deea8-127">Plats:</span><span class="sxs-lookup"><span data-stu-id="deea8-127">Where:</span></span>

- <span data-ttu-id="deea8-128">**Oooo** 2 – byte opcode-fält</span><span class="sxs-lookup"><span data-stu-id="deea8-128">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="deea8-129">0x0001-> öppen för läsning</span><span class="sxs-lookup"><span data-stu-id="deea8-129">0x0001 -> Open for read</span></span>  
<span data-ttu-id="deea8-130">0x0002-> öppna för skrivning</span><span class="sxs-lookup"><span data-stu-id="deea8-130">0x0002 -> Open for write</span></span>

- <span data-ttu-id="deea8-131">**f...** fält för f-byte-filnamn</span><span class="sxs-lookup"><span data-stu-id="deea8-131">**f…f** n-byte Filename field</span></span>

- <span data-ttu-id="deea8-132">0 1 – byte NULL avslutnings Character</span><span class="sxs-lookup"><span data-stu-id="deea8-132">0  1-byte NULL termination character</span></span>

- <span data-ttu-id="deea8-133">**Oktett** ASCII "OKTETT" för att ange binär överföring</span><span class="sxs-lookup"><span data-stu-id="deea8-133">**OCTET** ASCII “OCTET” to specify binary transfer</span></span>

- <span data-ttu-id="deea8-134">0 1 – byte NULL avslutnings Character</span><span class="sxs-lookup"><span data-stu-id="deea8-134">0  1-byte NULL termination character</span></span>

<span data-ttu-id="deea8-135">Definitionen av TFTP Write-, ACK-och fel meddelanden skiljer sig något från varandra och definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="deea8-135">The definition of the TFTP write, ACK, and error messages are slightly different and are defined as follows:</span></span>

<span data-ttu-id="deea8-136">**oooobbbbd... styr**</span><span class="sxs-lookup"><span data-stu-id="deea8-136">**oooobbbbd…d**</span></span>

<span data-ttu-id="deea8-137">Plats:</span><span class="sxs-lookup"><span data-stu-id="deea8-137">Where:</span></span>

- <span data-ttu-id="deea8-138">**Oooo** 2 – byte opcode-fält</span><span class="sxs-lookup"><span data-stu-id="deea8-138">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="deea8-139">0x0003-> data paket</span><span class="sxs-lookup"><span data-stu-id="deea8-139">0x0003 -> Data packet</span></span>  
<span data-ttu-id="deea8-140">0x0004 – > ACK för senaste läsning</span><span class="sxs-lookup"><span data-stu-id="deea8-140">0x0004 -> ACK for last read</span></span>  
<span data-ttu-id="deea8-141">0x0005 – fel villkor för ></span><span class="sxs-lookup"><span data-stu-id="deea8-141">0x0005 -> Error condition</span></span>  

- <span data-ttu-id="deea8-142">**bbbb** 2-byte block Number (1-n)</span><span class="sxs-lookup"><span data-stu-id="deea8-142">**bbbb** 2-byte Block Number field (1-n)</span></span>

- <span data-ttu-id="deea8-143">**d...** data fält för d n-byte</span><span class="sxs-lookup"><span data-stu-id="deea8-143">**d…d** n-byte Data field</span></span>


- <span data-ttu-id="deea8-144">0x0001 (Läs) fil namn 0 OKTETT 0</span><span class="sxs-lookup"><span data-stu-id="deea8-144">0x0001 (read) File Name 0 OCTET 0</span></span>

- <span data-ttu-id="deea8-145">0x0002 (Skriv) fil namn 0 OKTETT 0</span><span class="sxs-lookup"><span data-stu-id="deea8-145">0x0002 (write) File Name 0 OCTET 0</span></span>

## <a name="tftp-communication"></a><span data-ttu-id="deea8-146">TFTP-kommunikation</span><span class="sxs-lookup"><span data-stu-id="deea8-146">TFTP Communication</span></span>

<span data-ttu-id="deea8-147">TFTP-servrar använder välkända UDP-port 69 för att lyssna efter klient förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="deea8-147">TFTP Servers utilize the well-known UDP port 69 to listen for Client requests.</span></span> <span data-ttu-id="deea8-148">TFTP-klientens Sockets kan bindas till valfri tillgänglig UDP-port.</span><span class="sxs-lookup"><span data-stu-id="deea8-148">TFTP Client sockets may bind to any available UDP port.</span></span> <span data-ttu-id="deea8-149">Data paketets nytto last som innehåller filen som ska laddas upp eller hämtas skickas i 512 byte-segment tills det sista paketet som innehåller < 512 byte.</span><span class="sxs-lookup"><span data-stu-id="deea8-149">Data packet payload containing the file to upload or download is sent in 512 byte chunks, until the last packet containing < 512 bytes.</span></span> <span data-ttu-id="deea8-150">Ett paket som innehåller färre än 512 byte signalerar därför slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="deea8-150">Therefore a packet containing fewer than 512 bytes signals the end of file.</span></span> <span data-ttu-id="deea8-151">Den allmänna sekvensen av händelser är följande:</span><span class="sxs-lookup"><span data-stu-id="deea8-151">The general sequence of events is as follows:</span></span>

<span data-ttu-id="deea8-152">TFTP-Läs fil begär Anden:</span><span class="sxs-lookup"><span data-stu-id="deea8-152">TFTP Read File Requests:</span></span>

1.  <span data-ttu-id="deea8-153">Klienten utfärdar en "öppen för läsning"-begäran med fil namnet och väntar på ett svar från servern.</span><span class="sxs-lookup"><span data-stu-id="deea8-153">The Client issues an “Open For Read” request with the file name and waits for a reply from the Server.</span></span>

2.  <span data-ttu-id="deea8-154">Servern skickar den första 512 byten av filen eller mindre om fil storleken är mindre än 512 byte.</span><span class="sxs-lookup"><span data-stu-id="deea8-154">The Server sends the first 512 bytes of the file or less if the file size is less than 512 bytes.</span></span>

3.  <span data-ttu-id="deea8-155">Klienten tar emot data, skickar en bekräftelse och väntar på nästa paket från servern för filer som innehåller mer än 512 byte.</span><span class="sxs-lookup"><span data-stu-id="deea8-155">The Client receives data, sends an ACK, and waits for the next packet from the Server for files containing more than 512 bytes.</span></span>

4.  <span data-ttu-id="deea8-156">Sekvensen slutar när klienten tar emot ett paket som innehåller färre än 512 byte.</span><span class="sxs-lookup"><span data-stu-id="deea8-156">The sequence ends when the Client receives a packet containing fewer than 512 bytes.</span></span>

<span data-ttu-id="deea8-157">TFTP-Skriv begär Anden:</span><span class="sxs-lookup"><span data-stu-id="deea8-157">TFTP Write Requests:</span></span>

1.  <span data-ttu-id="deea8-158">Klienten utfärdar en "öppen för skrivning"-begäran med fil namnet och väntar på en bekräftelse med block antalet 0 från servern.</span><span class="sxs-lookup"><span data-stu-id="deea8-158">The Client issues an “Open for Write” request with the file name and waits for an ACK with a block number of 0 from the Server.</span></span>

2.  <span data-ttu-id="deea8-159">När servern är redo att skriva filen skickas en bekräftelse med ett block antal noll.</span><span class="sxs-lookup"><span data-stu-id="deea8-159">When the Server is ready to write the file, it sends an ACK with a block number of zero.</span></span>

3.  <span data-ttu-id="deea8-160">Klienten skickar de första 512 byten av filen (eller mindre för filer som är mindre än 512 byte) till servern och väntar på en ACK tillbaka.</span><span class="sxs-lookup"><span data-stu-id="deea8-160">The Client sends the first 512 bytes of the file (or less for files less than 512 bytes) to the Server and waits for an ACK back.</span></span>

4.  <span data-ttu-id="deea8-161">Servern skickar en ACK efter att byte har skrivits.</span><span class="sxs-lookup"><span data-stu-id="deea8-161">The Server sends an ACK after the bytes are written.</span></span>

5.  <span data-ttu-id="deea8-162">Sekvensen slutar när klienten har skrivit ett paket som innehåller färre än 512 byte.</span><span class="sxs-lookup"><span data-stu-id="deea8-162">The sequence ends when the Client completes writing a packet containing fewer than 512 bytes.</span></span>
 

## <a name="tftp-server-session-timer"></a><span data-ttu-id="deea8-163">Timer för TFTP-serversessionen</span><span class="sxs-lookup"><span data-stu-id="deea8-163">TFTP Server Session Timer</span></span>

<span data-ttu-id="deea8-164">TFTP-servern har ett begränsat antal klient begär ande platser.</span><span class="sxs-lookup"><span data-stu-id="deea8-164">The TFTP Server has a limited number of client request slots.</span></span> <span data-ttu-id="deea8-165">Om en klientsession verkar släppas, kan den platsen inte vara tillgänglig för åter användning.</span><span class="sxs-lookup"><span data-stu-id="deea8-165">If a client session appears to be dropped, that slot cannot be available for re-use.</span></span> <span data-ttu-id="deea8-166">Om NX_TFTP_SERVER_RETRANSMIT_ENABLE alternativet är aktive rad skapar dock NetX Duo TFTP-servern en session-timer som övervakar tids gränsen för var och en av dess klientsessioner.</span><span class="sxs-lookup"><span data-stu-id="deea8-166">However if the NX_TFTP_SERVER_RETRANSMIT_ENABLE option is enabled, the NetX Duo TFTP Server creates an session timer that monitors the timeout on each of its client sessions.</span></span> <span data-ttu-id="deea8-167">När tids gränsen för sessionen upphör att gälla avslutas den och alla öppna filer stängs.</span><span class="sxs-lookup"><span data-stu-id="deea8-167">When a session timeout expires it is terminated and any open files are closed.</span></span> <span data-ttu-id="deea8-168">Facket blir därför tillgängligt för en annan TFTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="deea8-168">Thus the ‘slot’ becomes available for another TFTP Client request.</span></span>

<span data-ttu-id="deea8-169">Om du vill ange tids gränsen justerar du konfigurations alternativet NX_TFTP_SERVER_RETRANSMIT_TIMEOUT som som standard är 200 timer-Tick.</span><span class="sxs-lookup"><span data-stu-id="deea8-169">To set the timeout, adjust the configuration option NX_TFTP_SERVER_RETRANSMIT_TIMEOUT which by default is 200 timer ticks.</span></span> <span data-ttu-id="deea8-170">Intervallet mellan vilka sessions-timeout-värden kontrol leras anges av NX_TFTP_SERVER_TIMEOUT_PERIOD som är 20 timer-Tick som standard.</span><span class="sxs-lookup"><span data-stu-id="deea8-170">The interval between which session timeouts are checked is set by the NX_TFTP_SERVER_TIMEOUT_PERIOD which is 20 timer ticks by default.</span></span>

<span data-ttu-id="deea8-171">När TFTP-klienten har laddat upp (skrivna) filer till TFTP FileX-mediet, måste mediet rensas så att data kan skrivas från TFTP-serverns RAM-disk till det underliggande mediet (TFTP-klientens disk minne).</span><span class="sxs-lookup"><span data-stu-id="deea8-171">When the TFTP Client has uploaded (written) files to the TFTP FileX media, the media needs to be flushed so that data can be written from the TFTP server ram disk to the underlying media (TFTP Client disk memory).</span></span> <span data-ttu-id="deea8-172">Detta kan göras med hjälp av fx_media_flush tjänsten om programmet inte vill stänga TFTP-servern.</span><span class="sxs-lookup"><span data-stu-id="deea8-172">This can be done using the fx_media_flush service if the application does not wish to close the TFTP Server.</span></span>

<span data-ttu-id="deea8-173">Men när du har stängt TFTP-servern bör programmet, om det inte har någon annan användning för FileX-mediet, stänga mediet med hjälp av tjänsten fx_media_close.</span><span class="sxs-lookup"><span data-stu-id="deea8-173">However, after closing the TFTP server, the application should, if it has no further use for the FileX media, then close the media using the fx_media_close service.</span></span> <span data-ttu-id="deea8-174">Detta tömmer fil data tillbaka till TFTP-klientdatorn, stänger öppna filer och uppdaterar katalog informationen till mediet.</span><span class="sxs-lookup"><span data-stu-id="deea8-174">This will flush the file data back to the TFTP Client disk, close open files, and update the directory information to the media.</span></span>

<span data-ttu-id="deea8-175">Avsnittet "små exempel" i det här kapitlet visar detta.</span><span class="sxs-lookup"><span data-stu-id="deea8-175">The “Small Example” section in this chapter demonstrates this.</span></span>

<span data-ttu-id="deea8-176">Ett tredje alternativ för att uppdatera FileX-mediet är att kompilera FileX-biblioteket med FX_FAULT_TOLERANT eller FX_FAULT_TOLERANT_DATA alternativ i stället för att använda FileX-tjänster explicit.</span><span class="sxs-lookup"><span data-stu-id="deea8-176">A third option for updating the FileX media is to compile the FileX library with the FX_FAULT_TOLERANT or the FX_FAULT_TOLERANT_DATA options instead of using FileX services explicitly.</span></span> <span data-ttu-id="deea8-177">Om det har definierats skickar FileX automatiskt Skriv förfrågningar till medie driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="deea8-177">If defined, FileX automatically passes write requests to the media driver.</span></span> <span data-ttu-id="deea8-178">De här alternativen kan begränsa prestanda men ger bättre skydd mot förlorade fildata eller förlorade kluster.</span><span class="sxs-lookup"><span data-stu-id="deea8-178">These options may limit performance but offer greater protection from lost file data or lost clusters.</span></span> <span data-ttu-id="deea8-179">Mer information om detta och FileX i allmänhet finns i användar handboken för Express Logic FileX.</span><span class="sxs-lookup"><span data-stu-id="deea8-179">For more information about this and FileX in general, please see the Express Logic FileX User Guide.</span></span>

## <a name="tftp-multi-thread-support"></a><span data-ttu-id="deea8-180">Stöd för TFTP-flera trådar</span><span class="sxs-lookup"><span data-stu-id="deea8-180">TFTP Multi-Thread Support</span></span>

<span data-ttu-id="deea8-181">Klient tjänsterna NetX Duo TFTP kan anropas från flera trådar samtidigt.</span><span class="sxs-lookup"><span data-stu-id="deea8-181">The NetX Duo TFTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="deea8-182">Läs-eller Skriv begär Anden för en viss TFTP-serverinstans bör dock göras i följd från samma tråd.</span><span class="sxs-lookup"><span data-stu-id="deea8-182">However, read or write requests for a particular TFTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="tftp-rfcs"></a><span data-ttu-id="deea8-183">TFTP-rapporter</span><span class="sxs-lookup"><span data-stu-id="deea8-183">TFTP RFCs</span></span>

<span data-ttu-id="deea8-184">NetX Duo TFTP är kompatibelt med RFC1350 och relaterade RFC: er.</span><span class="sxs-lookup"><span data-stu-id="deea8-184">NetX Duo TFTP is compliant with RFC1350 and related RFCs.</span></span>

