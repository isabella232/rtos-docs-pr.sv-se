---
title: Kapitel 1 – Introduktion till NetX HTTP
description: I det här dokumentet beskrivs hur HTTP är ett protokoll som har utformats för att överföra innehåll på webben.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826718"
---
# <a name="chapter-1---introduction-to-netx-http"></a><span data-ttu-id="94a82-103">Kapitel 1 – Introduktion till NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="94a82-103">Chapter 1 - Introduction to NetX HTTP</span></span>

<span data-ttu-id="94a82-104">Hypertext Transfer Protocol (HTTP) är ett protokoll som har utformats för att överföra innehåll på webben.</span><span class="sxs-lookup"><span data-stu-id="94a82-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="94a82-105">HTTP är ett enkelt protokoll som använder Reliable Transmission Control Protocol (TCP)-tjänster för att utföra sin innehålls överförings funktion.</span><span class="sxs-lookup"><span data-stu-id="94a82-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="94a82-106">Därför är HTTP ett mycket tillförlitligt innehålls överförings protokoll.</span><span class="sxs-lookup"><span data-stu-id="94a82-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="94a82-107">HTTP är ett av de mest använda program protokollen.</span><span class="sxs-lookup"><span data-stu-id="94a82-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="94a82-108">Alla åtgärder på webben använder HTTP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="94a82-108">All operations on the Web utilize the HTTP protocol.</span></span>

## <a name="http-requirements"></a><span data-ttu-id="94a82-109">HTTP-krav</span><span class="sxs-lookup"><span data-stu-id="94a82-109">HTTP Requirements</span></span>

<span data-ttu-id="94a82-110">För att kunna fungera korrekt kräver HTTP-paketet NetX att en NetX (version 5,2 eller senare) är installerad.</span><span class="sxs-lookup"><span data-stu-id="94a82-110">In order to function properly, the NetX HTTP package requires that a NetX (version 5.2 or later) is installed.</span></span> <span data-ttu-id="94a82-111">Dessutom måste en IP-instans redan skapas och TCP måste vara aktiverat på samma IP-instans.</span><span class="sxs-lookup"><span data-stu-id="94a82-111">In addition, an IP instance must already be created and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="94a82-112">Demo filen i avsnittet "litet exempel system" i **kapitel 2** visar hur detta görs.</span><span class="sxs-lookup"><span data-stu-id="94a82-112">The demo file in section “Small Example System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="94a82-113">HTTP-klient delen av NetX HTTP-paketet har inga ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="94a82-113">The HTTP Client portion of the NetX HTTP package has no further requirements.</span></span>

<span data-ttu-id="94a82-114">HTTP-server delen av NetX HTTP-paketet har flera ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="94a82-114">The HTTP Server portion of the NetX HTTP package has several additional requirements.</span></span> <span data-ttu-id="94a82-115">Först måste du ha fullständig åtkomst till den *välkända TCP-porten 80* för att hantera alla klient-HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="94a82-115">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests.</span></span> <span data-ttu-id="94a82-116">HTTP-servern är också avsedd att användas med det inbäddade fil systemet FileX.</span><span class="sxs-lookup"><span data-stu-id="94a82-116">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="94a82-117">Om FileX inte är tillgängligt kan användaren hamna i de delar av FileX som används i sin egen miljö.</span><span class="sxs-lookup"><span data-stu-id="94a82-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="94a82-118">Detta beskrivs i senare avsnitt i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="94a82-118">This is discussed in later sections of this guide.</span></span>

## <a name="http-constraints"></a><span data-ttu-id="94a82-119">HTTP-begränsningar</span><span class="sxs-lookup"><span data-stu-id="94a82-119">HTTP Constraints</span></span> 

<span data-ttu-id="94a82-120">NetX HTTP-protokollet implementerar HTTP 1,0-standarden.</span><span class="sxs-lookup"><span data-stu-id="94a82-120">The NetX HTTP protocol implements the HTTP 1.0 standard.</span></span> <span data-ttu-id="94a82-121">Det finns dock följande begränsningar:</span><span class="sxs-lookup"><span data-stu-id="94a82-121">However, there are following constraints:</span></span>

1.  <span data-ttu-id="94a82-122">Beständiga anslutningar stöds inte</span><span class="sxs-lookup"><span data-stu-id="94a82-122">Persistent connections are not supported</span></span>

2.  <span data-ttu-id="94a82-123">Pipelining för begäran stöds inte</span><span class="sxs-lookup"><span data-stu-id="94a82-123">Request pipelining is not supported</span></span>

3.  <span data-ttu-id="94a82-124">HTTP-servern stöder både Basic-och MD5 Digest-autentisering, men inte MD5-sess.</span><span class="sxs-lookup"><span data-stu-id="94a82-124">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="94a82-125">HTTP-klienten har nu bara stöd för grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="94a82-125">At present, the HTTP Client supports only basic authentication.</span></span>

4.  <span data-ttu-id="94a82-126">Det finns inte stöd för innehålls komprimering.</span><span class="sxs-lookup"><span data-stu-id="94a82-126">No content compression is supported.</span></span>

5.  <span data-ttu-id="94a82-127">SPÅRNINGs-, alternativ-och ANSLUTNINGS begär Anden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="94a82-127">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>

6.  <span data-ttu-id="94a82-128">Den modempool som är kopplad till HTTP-servern eller-klienten måste vara tillräckligt stor för att rymma det fullständiga HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="94a82-128">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>

7.  <span data-ttu-id="94a82-129">HTTP-klienttjänster är endast för innehålls överföring – det finns inga visnings verktyg i det här paketet.</span><span class="sxs-lookup"><span data-stu-id="94a82-129">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="94a82-130">HTTP-URL (resurs namn)</span><span class="sxs-lookup"><span data-stu-id="94a82-130">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="94a82-131">HTTP-protokollet är utformat för att överföra innehåll på webben.</span><span class="sxs-lookup"><span data-stu-id="94a82-131">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="94a82-132">Det begärda innehållet anges av URL: en (Universal Resource Locator).</span><span class="sxs-lookup"><span data-stu-id="94a82-132">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="94a82-133">Detta är den primära komponenten i varje HTTP-begäran.</span><span class="sxs-lookup"><span data-stu-id="94a82-133">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="94a82-134">URL: er börjar alltid med ett "/"-Character och motsvarar vanligt vis filer på HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="94a82-134">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="94a82-135">Vanliga HTTP-filtillägg visas nedan:</span><span class="sxs-lookup"><span data-stu-id="94a82-135">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="94a82-136">**. htm (eller. html)** Hypertext Markup Language (HTML)</span><span class="sxs-lookup"><span data-stu-id="94a82-136">**.htm (or .html)** Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="94a82-137">**. txt** Oformaterad ASCII-text</span><span class="sxs-lookup"><span data-stu-id="94a82-137">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="94a82-138">**. gif** Binär GIF-bild</span><span class="sxs-lookup"><span data-stu-id="94a82-138">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="94a82-139">**. XBM** Binär Xbitmap-avbildning</span><span class="sxs-lookup"><span data-stu-id="94a82-139">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="94a82-140">HTTP-klient begär Anden</span><span class="sxs-lookup"><span data-stu-id="94a82-140">HTTP Client Requests</span></span>

<span data-ttu-id="94a82-141">HTTP har en enkel mekanism för att begära webb innehåll.</span><span class="sxs-lookup"><span data-stu-id="94a82-141">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="94a82-142">Det finns i princip en uppsättning standard-HTTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den *välkända TCP-porten 80*.</span><span class="sxs-lookup"><span data-stu-id="94a82-142">There is basically a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80*.</span></span> <span data-ttu-id="94a82-143">Nedan visas några av de grundläggande HTTP-kommandona:</span><span class="sxs-lookup"><span data-stu-id="94a82-143">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="94a82-144">Hämta resurs HTTP/1.0 *Hämta den angivna resursen*</span><span class="sxs-lookup"><span data-stu-id="94a82-144">GET resource HTTP/1.0 *Get the specified resource*</span></span>
- <span data-ttu-id="94a82-145">PUBLICERA resurs HTTP/1.0 *Hämta den angivna resursen och skicka kopplade indata till HTTP-servern*</span><span class="sxs-lookup"><span data-stu-id="94a82-145">POST resource HTTP/1.0 *Get the specified resource and pass attached input to the HTTP Server*</span></span>
- <span data-ttu-id="94a82-146">HUVUD resurs-HTTP/1.0, *som behandlas som en get men inte innehåll, returneras av HTTP-servern*</span><span class="sxs-lookup"><span data-stu-id="94a82-146">HEAD resource HTTP/1.0 *Treated like a GET but not content is returned by the HTTP Server*</span></span>
- <span data-ttu-id="94a82-147">Placera resurs-HTTP/1.0-resurs *på HTTP-server*</span><span class="sxs-lookup"><span data-stu-id="94a82-147">PUT resource HTTP/1.0 *Place resource on HTTP Server*</span></span>
- <span data-ttu-id="94a82-148">TA bort resurs HTTP/1.0 *ta bort resurs på servern*</span><span class="sxs-lookup"><span data-stu-id="94a82-148">DELETE resource HTTP/1.0 *Delete resource on the Server*</span></span>

<span data-ttu-id="94a82-149">Dessa ASCII-kommandon genereras internt av webbläsare och NetX HTTP-klienttjänster för att utföra HTTP-åtgärder med en HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="94a82-149">These ASCII commands are generated internally by Web browsers and the NetX HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

>[!NOTE] 
> <span data-ttu-id="94a82-150">HTTP-klientens program som standard till Connect-porten 80.</span><span class="sxs-lookup"><span data-stu-id="94a82-150">The HTTP Client application default to the connect port of 80.</span></span> <span data-ttu-id="94a82-151">Det kan dock ändra anslutnings porten till HTTP-servern vid körning med hjälp av tjänsten *nx_http_client_set_connect_port* .</span><span class="sxs-lookup"><span data-stu-id="94a82-151">However, it can change the connect port to the HTTP Server at runtime using the *nx_http_client_set_connect_port* service.</span></span> <span data-ttu-id="94a82-152">Mer information om den här tjänsten finns i kapitel 4.</span><span class="sxs-lookup"><span data-stu-id="94a82-152">See Chapter 4 for more details of this service.</span></span> <span data-ttu-id="94a82-153">Detta är att hantera webb servrar som ibland använder alternativa portar för klient anslutningar.</span><span class="sxs-lookup"><span data-stu-id="94a82-153">This is to accommodate web servers that occasionally use alternate ports for Client connections.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="94a82-154">Svar på HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="94a82-154">HTTP Server Responses</span></span>

<span data-ttu-id="94a82-155">HTTP-servern använder samma *välkända TCP-port 80* för att skicka svar på klient kommandon.</span><span class="sxs-lookup"><span data-stu-id="94a82-155">The HTTP Server utilizes the same *well-known TCP port 80* to send Client command responses.</span></span> <span data-ttu-id="94a82-156">När HTTP-servern bearbetar klient kommandot returneras en ASCII-svarskod som innehåller en tresiffrig numerisk status kod.</span><span class="sxs-lookup"><span data-stu-id="94a82-156">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="94a82-157">Det numeriska svaret används av HTTP-klientens program vara för att avgöra om åtgärden lyckades eller misslyckades.</span><span class="sxs-lookup"><span data-stu-id="94a82-157">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="94a82-158">Nedan visas en lista över olika HTTP-server svar på klient kommandon:</span><span class="sxs-lookup"><span data-stu-id="94a82-158">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="94a82-159">200 *begäran har slutförts*</span><span class="sxs-lookup"><span data-stu-id="94a82-159">200 *Request was successful*</span></span>
- <span data-ttu-id="94a82-160">400- *begäran har inte formaterats korrekt*</span><span class="sxs-lookup"><span data-stu-id="94a82-160">400 *Request was not formed properly*</span></span>
- <span data-ttu-id="94a82-161">401 *obehörig begäran, klienten måste skicka autentisering*</span><span class="sxs-lookup"><span data-stu-id="94a82-161">401 *Unauthorized request, client needs to send authentication*</span></span>
- <span data-ttu-id="94a82-162">det *gick inte att hitta den angivna resursen i* 404</span><span class="sxs-lookup"><span data-stu-id="94a82-162">404 *Specified resource in request was not found*</span></span>
- <span data-ttu-id="94a82-163">500 *internt HTTP-server fel*</span><span class="sxs-lookup"><span data-stu-id="94a82-163">500 *Internal HTTP Server error*</span></span>
- <span data-ttu-id="94a82-164">501 *-begäran har inte implementerats av HTTP-servern*</span><span class="sxs-lookup"><span data-stu-id="94a82-164">501 *Request not implemented by HTTP Server*</span></span>
- <span data-ttu-id="94a82-165">502 *-tjänsten är inte tillgänglig*</span><span class="sxs-lookup"><span data-stu-id="94a82-165">502 *Service is not available*</span></span>

<span data-ttu-id="94a82-166">Till exempel är en lyckad klientbegäran att skicka filen "test.htm" svars med meddelandet "HTTP/1.0 200 OK".</span><span class="sxs-lookup"><span data-stu-id="94a82-166">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.0 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="94a82-167">HTTP-kommunikation</span><span class="sxs-lookup"><span data-stu-id="94a82-167">HTTP Communication</span></span>

<span data-ttu-id="94a82-168">Som tidigare nämnts använder HTTP-servern den *välkända TCP-port 80* för fält klient begär Anden.</span><span class="sxs-lookup"><span data-stu-id="94a82-168">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80* to field Client requests.</span></span> <span data-ttu-id="94a82-169">HTTP-klienter kan använda alla tillgängliga TCP-portar.</span><span class="sxs-lookup"><span data-stu-id="94a82-169">HTTP Clients may use any available TCP port.</span></span> <span data-ttu-id="94a82-170">Den allmänna sekvensen av HTTP-händelser är följande:</span><span class="sxs-lookup"><span data-stu-id="94a82-170">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="94a82-171">**Http GET-begäran**:</span><span class="sxs-lookup"><span data-stu-id="94a82-171">**HTTP GET Request**:</span></span>

1.  <span data-ttu-id="94a82-172">Klient problem TCP Anslut till server port 80.</span><span class="sxs-lookup"><span data-stu-id="94a82-172">Client issues TCP connect to Server port 80.</span></span>

2.  <span data-ttu-id="94a82-173">Klienten skickar begäran om att **få resurs-http/1.0**(tillsammans med annan rubrik information).</span><span class="sxs-lookup"><span data-stu-id="94a82-173">Client sends “**GET resource HTTP/1.0**” request (along with other header information).</span></span>

3.  <span data-ttu-id="94a82-174">Servern skapar ett "**http/1.0 200 OK"-** meddelande med ytterligare information som omedelbart följs av resurs innehållet (om det finns några).</span><span class="sxs-lookup"><span data-stu-id="94a82-174">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>

4.  <span data-ttu-id="94a82-175">Servern utför en från koppling.</span><span class="sxs-lookup"><span data-stu-id="94a82-175">Server performs a disconnection.</span></span>

5.  <span data-ttu-id="94a82-176">Klienten utför en från koppling.</span><span class="sxs-lookup"><span data-stu-id="94a82-176">Client performs a disconnection.</span></span>

<span data-ttu-id="94a82-177">**Http-begäran**:</span><span class="sxs-lookup"><span data-stu-id="94a82-177">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="94a82-178">Klient problem TCP Anslut till server port 80.</span><span class="sxs-lookup"><span data-stu-id="94a82-178">Client issues TCP connect to Server port 80.</span></span>

2. <span data-ttu-id="94a82-179">Klienten skickar begäran "**Placera resurs http/1.0**", tillsammans med annan rubrik information och följt av resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="94a82-179">Client sends “**PUT resource HTTP/1.0**” request, along with other header information, and followed by the resource content.</span></span>

3. <span data-ttu-id="94a82-180">Servern skapar ett "**http/1.0 200 OK"-** meddelande med ytterligare information som direkt åtföljs av resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="94a82-180">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content.</span></span>

4. <span data-ttu-id="94a82-181">Servern utför en från koppling.</span><span class="sxs-lookup"><span data-stu-id="94a82-181">Server performs a disconnection.</span></span>

5. <span data-ttu-id="94a82-182">Klienten utför en från koppling.</span><span class="sxs-lookup"><span data-stu-id="94a82-182">Client performs a disconnection.</span></span>

>[!NOTE] 
> <span data-ttu-id="94a82-183">Som tidigare nämnts kan HTTP-klienten ändra standard anslutnings porten från 80 till en annan port med hjälp av *nx_http_client_set_connect_port* för webb servrar som använder alternativa portar för att ansluta till klienter.</span><span class="sxs-lookup"><span data-stu-id="94a82-183">As mentioned previously, the HTTP Client can change the default connect port from 80 to another port using the *nx_http_client_set_connect_port* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="94a82-184">HTTP-autentisering</span><span class="sxs-lookup"><span data-stu-id="94a82-184">HTTP Authentication</span></span>

<span data-ttu-id="94a82-185">HTTP-autentisering är valfritt och krävs inte för alla webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="94a82-185">HTTP authentication is optional and isn’t required for all Web requests.</span></span> <span data-ttu-id="94a82-186">Det finns två varianter-autentisering, nämligen *Basic* och *Digest*.</span><span class="sxs-lookup"><span data-stu-id="94a82-186">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="94a82-187">Grundläggande autentisering motsvarar autentisering med *namn* och *lösen ord* som finns i många protokoll.</span><span class="sxs-lookup"><span data-stu-id="94a82-187">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="94a82-188">I HTTP Basic-autentisering sammanfogas namn och lösen ord och kodas i base64-format.</span><span class="sxs-lookup"><span data-stu-id="94a82-188">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="94a82-189">Den största nack delen med grundläggande autentisering är att namnet och lösen ordet skickas på ett öppet sätt i begäran.</span><span class="sxs-lookup"><span data-stu-id="94a82-189">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="94a82-190">Detta gör det något enkelt för namn och lösen ord att bli stulen.</span><span class="sxs-lookup"><span data-stu-id="94a82-190">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="94a82-191">Digest-autentisering löser problemet genom att aldrig skicka namnet och lösen ordet i begäran.</span><span class="sxs-lookup"><span data-stu-id="94a82-191">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="94a82-192">I stället används en algoritm för att härleda en 128-bitars nyckel eller sammanfattad från namnet, lösen ordet och annan information.</span><span class="sxs-lookup"><span data-stu-id="94a82-192">Instead, an algorithm is used to derive a 128-bit key or digest from the name, password, and other information.</span></span> <span data-ttu-id="94a82-193">NetX HTTP-Server stöder standardalgoritmen för MD5-sammandrag.</span><span class="sxs-lookup"><span data-stu-id="94a82-193">The NetX HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="94a82-194">När krävs autentisering?</span><span class="sxs-lookup"><span data-stu-id="94a82-194">When is authentication required?</span></span> <span data-ttu-id="94a82-195">I princip avgör HTTP-servern om en begärd resurs kräver autentisering.</span><span class="sxs-lookup"><span data-stu-id="94a82-195">Basically, the HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="94a82-196">Om autentisering krävs och klientbegäran inte inkluderade rätt autentisering, skickas svars tiden "HTTP/1.0 401" med den typ av autentisering som krävs skickas till klienten.</span><span class="sxs-lookup"><span data-stu-id="94a82-196">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.0 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="94a82-197">Klienten förväntas sedan skapa en ny begäran med korrekt autentisering.</span><span class="sxs-lookup"><span data-stu-id="94a82-197">The Client is then expected to form a new request with the proper authentication.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="94a82-198">Motanrop för HTTP-autentisering</span><span class="sxs-lookup"><span data-stu-id="94a82-198">HTTP Authentication Callback</span></span>

<span data-ttu-id="94a82-199">Som tidigare nämnts är HTTP-autentisering valfritt och krävs inte för alla webb överföringar.</span><span class="sxs-lookup"><span data-stu-id="94a82-199">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="94a82-200">Dessutom är autentiseringen vanligt vis resurs beroende.</span><span class="sxs-lookup"><span data-stu-id="94a82-200">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="94a82-201">Åtkomst till vissa resurser på servern kräver autentisering, medan andra inte gör det.</span><span class="sxs-lookup"><span data-stu-id="94a82-201">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="94a82-202">HTTP-NetX gör det möjligt för programmet att ange (via ***nx_http_server_create*** -anrop) en rutin för motringning av autentisering som anropas i början av hantering av varje http-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="94a82-202">The NetX HTTP Server package allows the application to specify (via the ***nx_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="94a82-203">Återanrops rutinen tillhandahåller NetX HTTP-servern med användar namnet, lösen ordet och sfär strängarna som är kopplade till resursen och returnerar den typ av autentisering som krävs.</span><span class="sxs-lookup"><span data-stu-id="94a82-203">The callback routine provides the NetX HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="94a82-204">Om ingen autentisering krävs för resursen ska återanropet av autentiseringen returnera värdet för **NX_HTTP_DONT_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="94a82-204">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="94a82-205">Annars, om grundläggande autentisering krävs för den angivna resursen, bör rutinen returnera **NX_HTTP_BASIC_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="94a82-205">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="94a82-206">Slutligen, om MD5 Digest-autentisering krävs, bör återanrops rutinen returnera **NX_HTTP_DIGEST_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="94a82-206">And finally, if MD5 digest authentication is required, the callback routine should return **NX_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="94a82-207">Om ingen autentisering krävs för någon resurs som tillhandahålls av HTTP-servern behövs inte återanropet och en NULL-pekare kan anges för HTTP-servern skapa samtal.</span><span class="sxs-lookup"><span data-stu-id="94a82-207">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="94a82-208">Formatet på appen för att autentisera återanrop är mycket enkelt och definieras nedan:</span><span class="sxs-lookup"><span data-stu-id="94a82-208">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

<span data-ttu-id="94a82-209">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="94a82-209">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="94a82-210">*request_type* Anger HTTP-klientbegäran, giltiga begär Anden definieras som:</span><span class="sxs-lookup"><span data-stu-id="94a82-210">*request_type* Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="94a82-211">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-211">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="94a82-212">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-212">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="94a82-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="94a82-214">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-214">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="94a82-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="94a82-216">*resurs* Angiven resurs har begärts.</span><span class="sxs-lookup"><span data-stu-id="94a82-216">*resource* Specific resource requested.</span></span>
- <span data-ttu-id="94a82-217">*namn* Mål för pekaren till det begärda användar namnet.</span><span class="sxs-lookup"><span data-stu-id="94a82-217">*name* Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="94a82-218">*lösen ord* Destination för pekaren till det lösen ord som krävs.</span><span class="sxs-lookup"><span data-stu-id="94a82-218">*password* Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="94a82-219">*sfär* Mål för pekaren till sfären för den här autentiseringen.</span><span class="sxs-lookup"><span data-stu-id="94a82-219">*realm* Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="94a82-220">Returvärdet för autentiseringsmetoden anger om autentisering krävs.</span><span class="sxs-lookup"><span data-stu-id="94a82-220">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="94a82-221">namn, lösen ord och domän pekare används inte om **NX_HTTP_DONT_AUTHENTICATE** returneras av rutinen för återanrop av autentisering.</span><span class="sxs-lookup"><span data-stu-id="94a82-221">name, password, and realm pointers are not used if **NX_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="94a82-222">Annars måste HTTP-serverns utvecklare se till att **NX_HTTP_MAX_USERNAME** och **NX_HTTP_MAX_PASSWORD** som definieras i *nx_http_server. h* är tillräckligt stora för det användar namn och lösen ord som anges i återanropet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="94a82-222">Otherwise the HTTP server developer must ensure that **NX_HTTP_MAX_USERNAME** and **NX_HTTP_MAX_PASSWORD** defined in *nx_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="94a82-223">Dessa är båda standardvärdena för storlek 20 tecken.</span><span class="sxs-lookup"><span data-stu-id="94a82-223">These are both defaulted to size 20 chars.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="94a82-224">HTTP ogiltigt användar namn/lösen ord för motringning</span><span class="sxs-lookup"><span data-stu-id="94a82-224">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="94a82-225">Det valfria ogiltigt användar namn/lösen ord för motringning i NetX HTTP-server anropas om HTTP-servern får en ogiltig kombination av användar namn och lösen ord i en klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="94a82-225">The optional invalid username/password callback in NetX HTTP Server is invoked if HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="94a82-226">Om HTTP-serverprogrammet registrerar ett återanrop med HTTP-servern anropas det om antingen grundläggande eller sammanfattad autentisering Miss lyckas *i nx_http_server_get_process*, i *nx_http_server_put_process* eller *i nx_http_server_delete_process.*</span><span class="sxs-lookup"><span data-stu-id="94a82-226">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_http_server_get_process*, in *nx_http_server_put_process,* or *in nx_http_server_delete_process.*</span></span>

<span data-ttu-id="94a82-227">För att registrera ett återanrop med HTTP-servern definieras följande tjänst i NetX HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="94a82-227">To register a callback with the HTTP server, the following service is defined in NetX HTTP Server.</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
<span data-ttu-id="94a82-228">Förfrågnings typerna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="94a82-228">The request types are defined as follows:</span></span>

- <span data-ttu-id="94a82-229">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-229">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="94a82-230">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-230">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="94a82-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="94a82-232">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-232">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="94a82-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="94a82-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="94a82-234">HTTP-infoga GMT-datum huvud återanrop</span><span class="sxs-lookup"><span data-stu-id="94a82-234">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="94a82-235">Det finns ett valfritt motanrop i NetX HTTP-server för att infoga en datum rubrik i dess svarsmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="94a82-235">There is an optional callback in NetX HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="94a82-236">Detta motanrop anropas när HTTP-servern svarar på en skicka-eller GET-begäran</span><span class="sxs-lookup"><span data-stu-id="94a82-236">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="94a82-237">För att registrera ett GMT-datum återanrop med HTTP-servern definieras följande tjänst i NetX HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="94a82-237">To register a GMT date callback with the HTTP server, the following service is defined in the NetX HTTP Server.</span></span>

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="94a82-238">Data typen NX_HTTP_SERVER_DATE definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="94a82-238">The NX_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="94a82-239">HTTP cache-information Hämta motringning</span><span class="sxs-lookup"><span data-stu-id="94a82-239">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="94a82-240">HTTP-servern har ett återanrop för att begära högsta ålder och datum från HTTP-programmet för en specifik resurs.</span><span class="sxs-lookup"><span data-stu-id="94a82-240">The HTTP Server has a callback to request the max age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="94a82-241">Den här informationen används för att avgöra om HTTP-servern skickar hela sidan som svar på en klient GET-begäran.</span><span class="sxs-lookup"><span data-stu-id="94a82-241">This information is used to determine if the HTTP server sends the entire page in response to a Client Get request.</span></span> <span data-ttu-id="94a82-242">Om den "om det har ändrats sedan" i klientbegäran inte hittas eller inte matchar datumet "senast ändrad" som returnerades av Get cache-återanropet, skickas hela sidan.</span><span class="sxs-lookup"><span data-stu-id="94a82-242">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="94a82-243">Följande tjänst definieras för att registrera återanropet med HTTP-servern:</span><span class="sxs-lookup"><span data-stu-id="94a82-243">To register the callback with the HTTP server the following service is defined:</span></span>

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a><span data-ttu-id="94a82-244">Stöd för HTTP-multipart</span><span class="sxs-lookup"><span data-stu-id="94a82-244">HTTP Multipart Support</span></span>

<span data-ttu-id="94a82-245">Multipurpose Internet Mail Extensions (MIME) ursprungligen avsåg SMTP-protokollet, men dess användning har spridit till HTTP.</span><span class="sxs-lookup"><span data-stu-id="94a82-245">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="94a82-246">MIME tillåter meddelanden som innehåller blandade meddelande typer (t. ex. image/jpg och text/plain) i samma meddelande.</span><span class="sxs-lookup"><span data-stu-id="94a82-246">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="94a82-247">NetX HTTP-server har lagt till tjänster för att fastställa innehålls typ i HTTP-meddelanden som innehåller MIME från klienten.</span><span class="sxs-lookup"><span data-stu-id="94a82-247">NetX HTTP Server has added services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="94a82-248">Om du vill aktivera stöd för HTTP-multipart och använda dessa tjänster måste konfigurations alternativet **NX_HTTP_MULTIPART_ENABLE** definieras.</span><span class="sxs-lookup"><span data-stu-id="94a82-248">To enable HTTP multipart support and use these services, the configuration option **NX_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="94a82-249">Mer information om hur du använder dessa tjänster finns i beskrivningen i kapitel 3 "Beskrivning av HTTP-tjänster".</span><span class="sxs-lookup"><span data-stu-id="94a82-249">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="94a82-250">Stöd för HTTP multi-threading</span><span class="sxs-lookup"><span data-stu-id="94a82-250">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="94a82-251">NetX HTTP-klienttjänster kan anropas från flera trådar samtidigt.</span><span class="sxs-lookup"><span data-stu-id="94a82-251">The NetX HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="94a82-252">Läs-eller Skriv begär Anden för en viss HTTP-klient måste dock göras i följd från samma tråd.</span><span class="sxs-lookup"><span data-stu-id="94a82-252">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="94a82-253">HTTP-RFC</span><span class="sxs-lookup"><span data-stu-id="94a82-253">HTTP RFCs</span></span>

<span data-ttu-id="94a82-254">NetX HTTP är kompatibelt med RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2581 "TCP överbelastnings kontroll", RFC 1122 "krav för Internet-värdar" och relaterade RFC: er.</span><span class="sxs-lookup"><span data-stu-id="94a82-254">NetX HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>