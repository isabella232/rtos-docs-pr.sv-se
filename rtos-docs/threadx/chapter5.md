---
title: Kapitel 5 – driv rutiner för Azure återställnings tider ThreadX
description: Det här kapitlet innehåller en beskrivning av enhets driv rutiner för Azure återställnings tider-ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2432b291f2b3fa7d6d798b8b4c187dd20b97db6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827357"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx"></a><span data-ttu-id="dba64-103">Kapitel 5 – driv rutiner för Azure återställnings tider ThreadX</span><span class="sxs-lookup"><span data-stu-id="dba64-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX</span></span>

<span data-ttu-id="dba64-104">Det här kapitlet innehåller en beskrivning av enhets driv rutiner för Azure återställnings tider-ThreadX.</span><span class="sxs-lookup"><span data-stu-id="dba64-104">This chapter contains a description of device drivers for Azure RTOS ThreadX.</span></span> <span data-ttu-id="dba64-105">Informationen som presenteras i det här kapitlet är utformad för att hjälpa utvecklare att skriva programspecifika driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="dba64-105">The information presented in this chapter is designed to help developers write application-specific drivers.</span></span>

## <a name="device-driver-introduction"></a><span data-ttu-id="dba64-106">Introduktion till driv rutin</span><span class="sxs-lookup"><span data-stu-id="dba64-106">Device Driver Introduction</span></span>

<span data-ttu-id="dba64-107">Kommunikation med den externa miljön är en viktig komponent i de flesta inbäddade program.</span><span class="sxs-lookup"><span data-stu-id="dba64-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="dba64-108">Den här kommunikationen sker via maskin varu enheter som är tillgängliga för den inbäddade program varan.</span><span class="sxs-lookup"><span data-stu-id="dba64-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="dba64-109">De program varu komponenter som ansvarar för att hantera sådana enheter kallas ofta för *enhets driv rutiner*.</span><span class="sxs-lookup"><span data-stu-id="dba64-109">The software components responsible for managing such devices are commonly called *device drivers*.</span></span>

<span data-ttu-id="dba64-110">Enhets driv rutiner i Embedded är real tids system program beroende av varandra.</span><span class="sxs-lookup"><span data-stu-id="dba64-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="dba64-111">Detta är sant för två huvudsakliga orsaker: den stora mångfalden av mål maskin vara och de lika stora prestanda kraven för program i real tid.</span><span class="sxs-lookup"><span data-stu-id="dba64-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="dba64-112">Därför är det praktiskt taget omöjligt att tillhandahålla en gemensam uppsättning driv rutiner som uppfyller kraven för varje program.</span><span class="sxs-lookup"><span data-stu-id="dba64-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="dba64-113">Av dessa skäl är informationen i det här kapitlet utformad för att hjälpa användare att anpassa driv rutiner för ThreadX-driv rutinen *från hylla* och skriva egna specifika driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="dba64-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="dba64-114">Driv rutins funktioner</span><span class="sxs-lookup"><span data-stu-id="dba64-114">Driver Functions</span></span>

<span data-ttu-id="dba64-115">ThreadX enhets driv rutiner består av åtta grundläggande funktionella områden, enligt följande.</span><span class="sxs-lookup"><span data-stu-id="dba64-115">ThreadX device drivers are composed of eight basic functional areas, as follows.</span></span>

- <span data-ttu-id="dba64-116">**Driv rutins initiering**</span><span class="sxs-lookup"><span data-stu-id="dba64-116">**Driver Initialization**</span></span>
- <span data-ttu-id="dba64-117">**Driv rutins kontroll**</span><span class="sxs-lookup"><span data-stu-id="dba64-117">**Driver Control**</span></span>
- <span data-ttu-id="dba64-118">**Driv rutins åtkomst**</span><span class="sxs-lookup"><span data-stu-id="dba64-118">**Driver Access**</span></span>
- <span data-ttu-id="dba64-119">**Driv rutins Indatatyp**</span><span class="sxs-lookup"><span data-stu-id="dba64-119">**Driver Input**</span></span>
- <span data-ttu-id="dba64-120">**Driv rutins utdata**</span><span class="sxs-lookup"><span data-stu-id="dba64-120">**Driver Output**</span></span>
- <span data-ttu-id="dba64-121">**Driv rutins avbrott**</span><span class="sxs-lookup"><span data-stu-id="dba64-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="dba64-122">**Driv rutins status**</span><span class="sxs-lookup"><span data-stu-id="dba64-122">**Driver Status**</span></span>
- <span data-ttu-id="dba64-123">**Driv rutins avslutning**</span><span class="sxs-lookup"><span data-stu-id="dba64-123">**Driver Termination**</span></span>

<span data-ttu-id="dba64-124">Med undantag för initiering, är varje funktions områden valfritt.</span><span class="sxs-lookup"><span data-stu-id="dba64-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="dba64-125">Dessutom är den exakta bearbetningen i varje zon specifika för enhets driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="dba64-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="dba64-126">Driv rutins initiering</span><span class="sxs-lookup"><span data-stu-id="dba64-126">Driver Initialization</span></span>
<span data-ttu-id="dba64-127">Det här funktions avsnittet ansvarar för initiering av den faktiska maskin varu enheten och de interna data strukturerna för driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="dba64-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="dba64-128">Det är inte tillåtet att anropa andra driv rutins tjänster förrän initieringen är klar.</span><span class="sxs-lookup"><span data-stu-id="dba64-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!NOTE]
> <span data-ttu-id="dba64-129">\* Driv Rutinens initierings funktions komponent anropas vanligt vis från \***tx_application_define** _-funktionen eller från en initierings Thread._</span><span class="sxs-lookup"><span data-stu-id="dba64-129">\*The driver's initialization function component is typically called from the \***tx_application_define** _ function or from an initialization thread._</span></span>

### <a name="driver-control"></a><span data-ttu-id="dba64-130">Driv rutins kontroll</span><span class="sxs-lookup"><span data-stu-id="dba64-130">Driver Control</span></span>

<span data-ttu-id="dba64-131">När driv rutinen har initierats och är klar för drift är det här funktions avsnittet ansvarigt för körnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="dba64-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="dba64-132">Vanligt vis består körnings kontroll av att göra ändringar i den underliggande maskin varu enheten.</span><span class="sxs-lookup"><span data-stu-id="dba64-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="dba64-133">Exempel på detta är att ändra överföringshastigheten för en seriell enhet eller att söka efter en ny sektor på en disk.</span><span class="sxs-lookup"><span data-stu-id="dba64-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="dba64-134">Driv rutins åtkomst</span><span class="sxs-lookup"><span data-stu-id="dba64-134">Driver Access</span></span>

<span data-ttu-id="dba64-135">Vissa enhets driv rutiner anropas bara från en enda program tråd.</span><span class="sxs-lookup"><span data-stu-id="dba64-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="dba64-136">I sådana fall behövs inte det här funktions fältet.</span><span class="sxs-lookup"><span data-stu-id="dba64-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="dba64-137">I program där flera trådar behöver åtkomst till samtidiga driv rutiner måste dock deras interaktion kontrol leras genom att lägga till tilldelnings-/publicerings anläggningar i enhets driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="dba64-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="dba64-138">Alternativt kan programmet använda en semafor för att kontrol lera åtkomsten till driv rutinen och undvika extra kostnader i driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="dba64-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span>

### <a name="driver-input"></a><span data-ttu-id="dba64-139">Driv rutins Indatatyp</span><span class="sxs-lookup"><span data-stu-id="dba64-139">Driver Input</span></span>

<span data-ttu-id="dba64-140">Det här funktions avsnittet ansvarar för all enhets information.</span><span class="sxs-lookup"><span data-stu-id="dba64-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="dba64-141">Huvud problemen som är kopplade till driv rutins inflödet omfattar vanligt vis hur indatamängden buffras och hur trådar väntar på sådana indatatyper.</span><span class="sxs-lookup"><span data-stu-id="dba64-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span>

### <a name="driver-output"></a><span data-ttu-id="dba64-142">Driv rutins utdata</span><span class="sxs-lookup"><span data-stu-id="dba64-142">Driver Output</span></span>

<span data-ttu-id="dba64-143">Det här funktions avsnittet ansvarar för all enhets utdata.</span><span class="sxs-lookup"><span data-stu-id="dba64-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="dba64-144">Huvud problemen som är associerade med driv rutins utdata omfattar vanligt vis hur utdata buffras och hur trådar väntar på att utföra utdata.</span><span class="sxs-lookup"><span data-stu-id="dba64-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span>

### <a name="driver-interrupts"></a><span data-ttu-id="dba64-145">Driv rutins avbrott</span><span class="sxs-lookup"><span data-stu-id="dba64-145">Driver Interrupts</span></span>

<span data-ttu-id="dba64-146">De flesta real tids system är beroende av maskin varu avbrott för att meddela driv rutinen för enhetens indata, utdata, kontroll och fel händelser.</span><span class="sxs-lookup"><span data-stu-id="dba64-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="dba64-147">Avbrott ger en garanterad svars tid för sådana externa händelser.</span><span class="sxs-lookup"><span data-stu-id="dba64-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="dba64-148">I stället för avbrott kan driv rutins program varan regelbundet kontrol lera den externa maskin varan för sådana händelser.</span><span class="sxs-lookup"><span data-stu-id="dba64-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="dba64-149">Den här tekniken kallas *avsökning*.</span><span class="sxs-lookup"><span data-stu-id="dba64-149">This technique is called *polling*.</span></span> <span data-ttu-id="dba64-150">Det är mindre i real tid än avbrott, men avsökningen kan vara begriplig för vissa mindre real tids program.</span><span class="sxs-lookup"><span data-stu-id="dba64-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span>

### <a name="driver-status"></a><span data-ttu-id="dba64-151">Driv rutins status</span><span class="sxs-lookup"><span data-stu-id="dba64-151">Driver Status</span></span>

<span data-ttu-id="dba64-152">Detta funktions områden ansvarar för att tillhandahålla körnings status och statistik som är associerad med driv rutins åtgärden.</span><span class="sxs-lookup"><span data-stu-id="dba64-152">This function area is responsible for providing run-time status and statistics associated with the driver operation.</span></span> <span data-ttu-id="dba64-153">Information som hanteras av detta funktions områden innehåller vanligt vis följande.</span><span class="sxs-lookup"><span data-stu-id="dba64-153">Information managed by this function area typically includes the following.</span></span>

- <span data-ttu-id="dba64-154">Aktuell enhets status</span><span class="sxs-lookup"><span data-stu-id="dba64-154">Current device status</span></span>
- <span data-ttu-id="dba64-155">Inkommande byte</span><span class="sxs-lookup"><span data-stu-id="dba64-155">Input bytes</span></span>
- <span data-ttu-id="dba64-156">Antal utdata</span><span class="sxs-lookup"><span data-stu-id="dba64-156">Output bytes</span></span>
- <span data-ttu-id="dba64-157">Antal enhets fel</span><span class="sxs-lookup"><span data-stu-id="dba64-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="dba64-158">Driv rutins avslutning</span><span class="sxs-lookup"><span data-stu-id="dba64-158">Driver Termination</span></span>

<span data-ttu-id="dba64-159">Det här funktions fältet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="dba64-159">This functional area is optional.</span></span> <span data-ttu-id="dba64-160">Det krävs endast om driv rutinen och/eller den fysiska maskin varu enheten måste stängas av.</span><span class="sxs-lookup"><span data-stu-id="dba64-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="dba64-161">När den har avslut ATS får driv rutinen inte anropas igen förrän den har initierats om.</span><span class="sxs-lookup"><span data-stu-id="dba64-161">After being terminated, the driver must not be called again until it is reinitialized.</span></span>

## <a name="simple-driver-example"></a><span data-ttu-id="dba64-162">Exempel på enkel driv rutin</span><span class="sxs-lookup"><span data-stu-id="dba64-162">Simple Driver Example</span></span>

<span data-ttu-id="dba64-163">Ett exempel är det bästa sättet att beskriva en enhets driv rutin.</span><span class="sxs-lookup"><span data-stu-id="dba64-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="dba64-164">I det här exemplet förutsätter driv rutinen en enkel seriell maskin varu enhet med en konfigurations registrering, en inmatnings registrering och en utmatnings registrering.</span><span class="sxs-lookup"><span data-stu-id="dba64-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="dba64-165">Det här enkla driv rutins exemplet illustrerar funktions områdena initiering, indata, utdata och avbrott.</span><span class="sxs-lookup"><span data-stu-id="dba64-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="dba64-166">Enkel driv Rutins initiering</span><span class="sxs-lookup"><span data-stu-id="dba64-166">Simple Driver Initialization</span></span>

<span data-ttu-id="dba64-167">***Tx_sdriver_initialize*** funktionen för den enkla driv rutinen skapar två räknar semaforer som används för att hantera driv Rutinens indata-och utdata-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="dba64-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver's input and output operation.</span></span> <span data-ttu-id="dba64-168">Semaforen för indatamängden anges av den inmatade ISR när ett meddelande tas emot av den seriella maskin varu enheten.</span><span class="sxs-lookup"><span data-stu-id="dba64-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="dba64-169">Därför skapas indatamängds-semaforen med ett inledande antal noll.</span><span class="sxs-lookup"><span data-stu-id="dba64-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="dba64-170">I motsatsen anger utdata-semaforen tillgängligheten för den seriella maskin varu registreringen.</span><span class="sxs-lookup"><span data-stu-id="dba64-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="dba64-171">Den skapas med ett värde på en som anger att sändnings registreringen är tillgänglig först.</span><span class="sxs-lookup"><span data-stu-id="dba64-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="dba64-172">Initierings funktionen ansvarar också för att installera avbrotts vektor hanterare på låg nivå för aviseringar om indata och utdata.</span><span class="sxs-lookup"><span data-stu-id="dba64-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="dba64-173">Precis som andra ThreadX avbrotts tjänst rutiner måste den lägsta nivån anropa \***_tx_thread_context_save** _ innan du anropar ISR-drivrutinen för enkel driv rutin.</span><span class="sxs-lookup"><span data-stu-id="dba64-173">Like other ThreadX interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="dba64-174">När ISR-drivrutinen returnerar, måste den lågnivå hanteraren anropa _ \* _ _tx_thread_context_restore_\* \*.</span><span class="sxs-lookup"><span data-stu-id="dba64-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dba64-175">\* Det är viktigt att initiering anropas före någon av de andra driv rutins funktionerna.</span><span class="sxs-lookup"><span data-stu-id="dba64-175">\*It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="dba64-176">Normalt kallas driv rutins initiering från ***tx_application_define***.</span><span class="sxs-lookup"><span data-stu-id="dba64-176">Typically, driver initialization is called from ***tx_application_define***.</span></span>

```c
VOID tx_sdriver_initialize(VOID)
{
    /* Initialize the two counting semaphores used to control
    the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                        "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                        "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
    The initial vector handling should call the ISRs
    defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
    generation, baud rate, stop bits, etc. */
}
```
<span data-ttu-id="dba64-177">**BILD 9. Enkel driv Rutins initiering**</span><span class="sxs-lookup"><span data-stu-id="dba64-177">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="dba64-178">Enkel driv Rutins Indatatyp</span><span class="sxs-lookup"><span data-stu-id="dba64-178">Simple Driver Input</span></span>

<span data-ttu-id="dba64-179">Inmatade för enkla driv rutins Center kring semaforen för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="dba64-179">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="dba64-180">När ett avbrotts meddelande för seriell enhet tas emot anges indatamängden.</span><span class="sxs-lookup"><span data-stu-id="dba64-180">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="dba64-181">Om en eller flera trådar väntar på ett kort från driv rutinen fortsätter tråden att vänta den längsta tiden.</span><span class="sxs-lookup"><span data-stu-id="dba64-181">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="dba64-182">Om inga trådar väntar, förblir semaforen bara inställd tills en tråd anropar funktionen för enhets ingång.</span><span class="sxs-lookup"><span data-stu-id="dba64-182">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="dba64-183">Det finns flera begränsningar för den enkla hantering av driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="dba64-183">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="dba64-184">Det viktigaste är möjligheten att släppa indatavärden.</span><span class="sxs-lookup"><span data-stu-id="dba64-184">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="dba64-185">Detta kan bero på att det inte går att mata in indataportar som kommer innan föregående tecken bearbetas.</span><span class="sxs-lookup"><span data-stu-id="dba64-185">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="dba64-186">Detta hanteras enkelt genom att lägga till en buffert för inmatade Character.</span><span class="sxs-lookup"><span data-stu-id="dba64-186">This is easily handled by adding an input character buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="dba64-187">*Endast trådar kan anropa*  \* **tx_sdriver_input** _ _function. \*</span><span class="sxs-lookup"><span data-stu-id="dba64-187">*Only threads are allowed to call the* ***tx_sdriver_input** _ _function.*</span></span>

<span data-ttu-id="dba64-188">Bild 10 visar käll koden som är kopplad till enkel driv rutins Indatatyp.</span><span class="sxs-lookup"><span data-stu-id="dba64-188">Figure 10 shows the source code associated with simple driver input.</span></span>

```c
UCHAR tx_sdriver_input(VOID)
{
  /* Determine if there is a character waiting. If not,
  suspend. */
  tx_semaphore_get(&tx_sdriver_input_semaphore,
  TX_WAIT_FOREVER;

  /* Return character from serial RX hardware register. */
  return(*serial_hardware_input_ptr);
}
  VOID tx_sdriver_input_ISR(VOID)
{
  /* See if an input character notification is pending. */
  if (!tx_sdriver_input_semaphore.tx_semaphore_count)
  {
    /* If not, notify thread of an input character. */
    tx_semaphore_put(&tx_sdriver_input_semaphore);
  }
}
```
<span data-ttu-id="dba64-189">**BILD 10. Enkel driv Rutins Indatatyp**</span><span class="sxs-lookup"><span data-stu-id="dba64-189">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="dba64-190">Enkla driv Rutins utdata</span><span class="sxs-lookup"><span data-stu-id="dba64-190">Simple Driver Output</span></span>

<span data-ttu-id="dba64-191">Bearbetning av utdata använder semaforen för utdata till signal när den seriella enhetens sändnings register är kostnads fri.</span><span class="sxs-lookup"><span data-stu-id="dba64-191">Output processing utilizes the output semaphore to signal when the serial device's transmit register is free.</span></span> <span data-ttu-id="dba64-192">Innan ett utmatnings avstånd skrivs till enheten hämtas utdata-semaforen.</span><span class="sxs-lookup"><span data-stu-id="dba64-192">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="dba64-193">Om den inte är tillgänglig är den tidigare överföringen inte slutförd ännu.</span><span class="sxs-lookup"><span data-stu-id="dba64-193">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="dba64-194">Den ISR-uteffekten ansvarar för hantering av avbrotts överföringen.</span><span class="sxs-lookup"><span data-stu-id="dba64-194">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="dba64-195">Bearbetning av de utgångna ISR-beloppen för att ställa in semaforen för utdata och därmed tillåta utdata från ett annat.</span><span class="sxs-lookup"><span data-stu-id="dba64-195">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!NOTE]
> <span data-ttu-id="dba64-196">*Endast trådar kan anropa*  \* **tx_sdriver_output** _ _function. \*</span><span class="sxs-lookup"><span data-stu-id="dba64-196">*Only threads are allowed to call the* ***tx_sdriver_output** _ _function.*</span></span>

<span data-ttu-id="dba64-197">Bild 11 visar käll koden som är kopplad till enkla driv rutins utdata.</span><span class="sxs-lookup"><span data-stu-id="dba64-197">Figure 11 shows the source code associated with simple driver output.</span></span>

```c
VOID tx_sdriver_output(UCHAR alpha)
{
  /* Determine if the hardware is ready to transmit a
  character. If not, suspend until the previous output
  completes. */
  tx_semaphore_get(&tx_sdriver_output_semaphore,
                                          TX_WAIT_FOREVER);

  /* Send the character through the hardware. */
  *serial_hardware_output_ptr = alpha;
}
  
VOID tx_sdriver_output_ISR(VOID)
{
  /* Notify thread last character transmit is
  complete. */
  tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="dba64-198">**BILD 11. Enkla driv Rutins utdata**</span><span class="sxs-lookup"><span data-stu-id="dba64-198">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="dba64-199">Brister i enkla driv rutiner</span><span class="sxs-lookup"><span data-stu-id="dba64-199">Simple Driver Shortcomings</span></span>

<span data-ttu-id="dba64-200">Den här enkla driv rutins exemplet illustrerar den grundläggande idén med en ThreadX enhets driv rutin.</span><span class="sxs-lookup"><span data-stu-id="dba64-200">This simple device driver example illustrates the basic idea of a ThreadX device driver.</span></span> <span data-ttu-id="dba64-201">Men eftersom den enkla enhets driv rutinen inte hanterar DataBuffer eller eventuella problem, representerar den inte fullständigt verkliga ThreadX-drivrutiner.</span><span class="sxs-lookup"><span data-stu-id="dba64-201">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX drivers.</span></span> <span data-ttu-id="dba64-202">I följande avsnitt beskrivs några av de mer avancerade problem som är associerade med enhets driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="dba64-202">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="dba64-203">Problem med avancerad driv rutin</span><span class="sxs-lookup"><span data-stu-id="dba64-203">Advanced Driver Issues</span></span>

<span data-ttu-id="dba64-204">Som tidigare nämnts har enhets driv rutinerna krav som unika som program.</span><span class="sxs-lookup"><span data-stu-id="dba64-204">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="dba64-205">Vissa program kan kräva en enorma mängd databuffation, medan ett annat program kan kräva optimerad driv rutins ISR: er på grund av enhets avbrott med hög frekvens.</span><span class="sxs-lookup"><span data-stu-id="dba64-205">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="dba64-206">I/O-buffring</span><span class="sxs-lookup"><span data-stu-id="dba64-206">I/O Buffering</span></span>

<span data-ttu-id="dba64-207">Databuffring i inbäddade program i real tid kräver avsevärd planering.</span><span class="sxs-lookup"><span data-stu-id="dba64-207">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="dba64-208">En del av designen styrs av den underliggande maskin varu enheten.</span><span class="sxs-lookup"><span data-stu-id="dba64-208">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="dba64-209">Om enheten tillhandahåller grundläggande byte i/O är en enkel cirkulär buffert förmodligen i ordning.</span><span class="sxs-lookup"><span data-stu-id="dba64-209">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="dba64-210">Men om enheten tillhandahåller block-, DMA-eller paket-I/O är ett buffertminne förmodligen motiverat.</span><span class="sxs-lookup"><span data-stu-id="dba64-210">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span>

### <a name="circular-byte-buffers"></a><span data-ttu-id="dba64-211">Cirkelformade byte-buffertar</span><span class="sxs-lookup"><span data-stu-id="dba64-211">Circular Byte Buffers</span></span>

<span data-ttu-id="dba64-212">Cirkelformade byte-buffertar används vanligt vis i driv rutiner som hanterar en enkel seriell maskin varu enhet som en UART.</span><span class="sxs-lookup"><span data-stu-id="dba64-212">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="dba64-213">Två cirkelformade buffertar används oftast i sådana situationer – en för indata och en för utdata.</span><span class="sxs-lookup"><span data-stu-id="dba64-213">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="dba64-214">Varje cirkulär byte-buffert består av ett byte minnes utrymme (vanligt vis en matris av **UCHAR** s), en Läs pekare och en Skriv pekare.</span><span class="sxs-lookup"><span data-stu-id="dba64-214">Each circular byte buffer is comprised of a byte memory area (typically an array of **UCHAR** s), a read pointer, and a write pointer.</span></span> <span data-ttu-id="dba64-215">En buffert anses vara tom när Läs pekaren och skriv pekarna hänvisar till samma minnes plats i bufferten.</span><span class="sxs-lookup"><span data-stu-id="dba64-215">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="dba64-216">Driv rutins initiering anger både läsa-och skrivbara pekare till Start adressen för bufferten.</span><span class="sxs-lookup"><span data-stu-id="dba64-216">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="dba64-217">Cirkulära buffer-ingångar</span><span class="sxs-lookup"><span data-stu-id="dba64-217">Circular Buffer Input</span></span>

<span data-ttu-id="dba64-218">Indatabufferten används för att lagra tecken som kommer innan programmet är redo för dem.</span><span class="sxs-lookup"><span data-stu-id="dba64-218">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="dba64-219">När ett indatavärde tas emot (vanligt vis i ett Interrupt Service Routine), hämtas det nya specialtecknet från maskin varu enheten och placeras i indatabufferten vid den plats som pekas på av skriv pekaren.</span><span class="sxs-lookup"><span data-stu-id="dba64-219">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="dba64-220">Skriv pekaren är sedan avancerad till nästa position i bufferten.</span><span class="sxs-lookup"><span data-stu-id="dba64-220">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="dba64-221">Om nästa position är i slutet av bufferten anges skriv pekaren till början av bufferten.</span><span class="sxs-lookup"><span data-stu-id="dba64-221">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="dba64-222">Kön med fullständigt tillstånd hanteras genom att skriva pekare avbryts om den nya skriv pekaren är samma som Läs pekaren.</span><span class="sxs-lookup"><span data-stu-id="dba64-222">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="dba64-223">Begär Anden om programinspelnings-byte till driv rutinen kontrollerar först Läs-och skriv pekarna för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="dba64-223">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="dba64-224">Om Läs-och skriv pekarna är identiska är bufferten tom.</span><span class="sxs-lookup"><span data-stu-id="dba64-224">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="dba64-225">Annars, om Läs pekaren inte är densamma, kopieras den byte som pekas av Läs pekaren från indatabufferten och Läs pekaren är avancerad till nästa buffertplats.</span><span class="sxs-lookup"><span data-stu-id="dba64-225">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="dba64-226">Om den nya Läs pekaren överskrider buffertens slut återställs den till början.</span><span class="sxs-lookup"><span data-stu-id="dba64-226">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="dba64-227">Bild 12 visar logiken för den cirkelformade indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="dba64-227">Figure 12 shows the logic for the circular input buffer.</span></span>

```c
UCHAR   tx_input_buffer[MAX_SIZE];
UCHAR   tx_input_write_ptr;
UCHAR   tx_input_read_ptr;

/* Initialization. */
tx_input_write_ptr =    &tx_input_buffer[0];
tx_input_read_ptr =     &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr = tx_input_write_ptr;
*tx_input_write_ptr++ = alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr = &tx_input_buffer[0]; /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr = save_ptr; /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
  alpha = *tx_input_read_ptr++;
  if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
      tx_input_read_ptr = &tx_input_buffer[0];
}
```
<span data-ttu-id="dba64-228">**FIGUR 12. Logik för cirkulär inmatad buffert**</span><span class="sxs-lookup"><span data-stu-id="dba64-228">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!NOTE]
> <span data-ttu-id="dba64-229">\* För tillförlitlig åtgärd kan det vara nödvändigt att utelåsning av avbrott när du ändrar Läs-och skriv pekarna för både indata och utdata med cirkulära buffertar.</span><span class="sxs-lookup"><span data-stu-id="dba64-229">\*For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span> *

### <a name="circular-output-buffer"></a><span data-ttu-id="dba64-230">Cirkulär utdatabufferten</span><span class="sxs-lookup"><span data-stu-id="dba64-230">Circular Output Buffer</span></span>

<span data-ttu-id="dba64-231">Utdatabufferten används för att lagra tecken som har anlänt för utdata innan maskin varan har skickat tidigare byte.</span><span class="sxs-lookup"><span data-stu-id="dba64-231">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="dba64-232">Bearbetning av utdatabufferten fungerar på samma sätt som bearbetningen av indata-buffring, förutom att överföringen av avbrotts processen ändrar utdata till Läs-och utdata-pekaren, medan begäran om program utdata använder skriv pekaren för utdata.</span><span class="sxs-lookup"><span data-stu-id="dba64-232">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span>
<span data-ttu-id="dba64-233">Annars är bearbetningen av utdatabufferten densamma.</span><span class="sxs-lookup"><span data-stu-id="dba64-233">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="dba64-234">Bild 13 visar logiken för den cirkelformade utdatabufferten.</span><span class="sxs-lookup"><span data-stu-id="dba64-234">Figure 13 shows the logic for the circular output buffer.</span></span>

```c
UCHAR   tx_output_buffer[MAX_SIZE];
UCHAR   tx_output_write_ptr;
UCHAR   tx_output_read_ptr;

/* Initialization. */
tx_output_write_ptr = &tx_output_buffer[0];
tx_output_read_ptr = &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
  *device_reg = *tx_output_read_ptr++;
  if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
      tx_output_read_ptr = &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr = tx_output_write_ptr;
*tx_output_write_ptr++ = alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr = &tx_output_buffer[0]; /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr = save_ptr; /* Buffer full! */
```
<span data-ttu-id="dba64-235">**FIGUR 13. Logik för cirkelformad utdatabuffert**</span><span class="sxs-lookup"><span data-stu-id="dba64-235">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="dba64-236">I/O-hantering för buffert</span><span class="sxs-lookup"><span data-stu-id="dba64-236">Buffer I/O Management</span></span>

<span data-ttu-id="dba64-237">För att förbättra prestandan hos inbäddade mikroprocessorer, skickar många enheter för kring utrustning till och tar emot data med buffertar som tillhandahålls av program vara.</span><span class="sxs-lookup"><span data-stu-id="dba64-237">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="dba64-238">I vissa implementeringar kan flera buffertar användas för att skicka eller ta emot enskilda data paket.</span><span class="sxs-lookup"><span data-stu-id="dba64-238">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span>

<span data-ttu-id="dba64-239">Storlek och plats för I/O-buffertar bestäms av programmet och/eller driv rutins program varan.</span><span class="sxs-lookup"><span data-stu-id="dba64-239">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="dba64-240">Normalt är buffertar fasta i storlek och hanteras i en ThreadX block-lagringspool.</span><span class="sxs-lookup"><span data-stu-id="dba64-240">Typically, buffers are fixed in size and managed within a ThreadX block memory pool.</span></span> <span data-ttu-id="dba64-241">I bild 14 beskrivs en typisk I/O-buffert och en ThreadX block-pool som hanterar sin allokering.</span><span class="sxs-lookup"><span data-stu-id="dba64-241">Figure 14 describes a typical I/O buffer and a ThreadX block memory pool that manages their allocation.</span></span>

```c
typedef struct TX_IO_BUFFER_STRUCT
{
      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
      struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
"free_memory_ptr"points to an available memory area that
is 64 KBytes in size. */
tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```

<span data-ttu-id="dba64-242">**BILD 14. I/O-buffert**</span><span class="sxs-lookup"><span data-stu-id="dba64-242">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="dba64-243">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="dba64-243">TX_IO_BUFFER</span></span>

<span data-ttu-id="dba64-244">TypeDef-TX_IO_BUFFER består av två pekare.</span><span class="sxs-lookup"><span data-stu-id="dba64-244">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="dba64-245">**Tx_next_packets** pekaren används för att länka flera paket antingen i indata-eller utmatnings listan.</span><span class="sxs-lookup"><span data-stu-id="dba64-245">The **tx_next_packet** pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="dba64-246">**Tx_next_buffers** pekaren används för att länka samman buffertar som utgör ett enskilt data paket från enheten.</span><span class="sxs-lookup"><span data-stu-id="dba64-246">The **tx_next_buffer** pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="dba64-247">Båda dessa pekare är inställda på NULL när bufferten tilldelas från poolen.</span><span class="sxs-lookup"><span data-stu-id="dba64-247">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="dba64-248">Dessutom kan vissa enheter kräva ett annat fält för att ange hur mycket av buffertutrymme som faktiskt innehåller data.</span><span class="sxs-lookup"><span data-stu-id="dba64-248">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="dba64-249">Buffrad I/O-fördel</span><span class="sxs-lookup"><span data-stu-id="dba64-249">Buffered I/O Advantage</span></span>

<span data-ttu-id="dba64-250">Vilka är fördelarna med ett I/O-schema för bufferten?</span><span class="sxs-lookup"><span data-stu-id="dba64-250">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="dba64-251">Den största fördelen är att data inte kopieras mellan enhets registren och programmets minne.</span><span class="sxs-lookup"><span data-stu-id="dba64-251">The biggest advantage is that data is not copied between the device registers and the application's memory.</span></span> <span data-ttu-id="dba64-252">I stället tillhandahåller driv rutinen enheten med en serie buffertar.</span><span class="sxs-lookup"><span data-stu-id="dba64-252">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="dba64-253">Fysisk enhet I/O använder det tillhandahållna buffertminne direkt.</span><span class="sxs-lookup"><span data-stu-id="dba64-253">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="dba64-254">Att använda processorn för att kopiera indata eller utgående paket med information är mycket kostsam och bör undvikas i en hög genom strömnings-I/O-situation.</span><span class="sxs-lookup"><span data-stu-id="dba64-254">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="dba64-255">En annan fördel med den buffrade I/O-metoden är att indata-och utmatnings listor inte har fullständiga villkor.</span><span class="sxs-lookup"><span data-stu-id="dba64-255">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="dba64-256">Alla tillgängliga buffertar kan finnas i någon av listorna vid ett och samma tillfälle.</span><span class="sxs-lookup"><span data-stu-id="dba64-256">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="dba64-257">Detta skiljer sig åt cirkulära buffertar i enkla byte som presenteras tidigare i kapitlet.</span><span class="sxs-lookup"><span data-stu-id="dba64-257">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="dba64-258">Var och en hade en fast storlek som bestämts vid kompileringen.</span><span class="sxs-lookup"><span data-stu-id="dba64-258">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="dba64-259">Tillskrivs driv Rutins ansvar</span><span class="sxs-lookup"><span data-stu-id="dba64-259">Buffered Driver Responsibilities</span></span>

<span data-ttu-id="dba64-260">Buffrade enhets driv rutiner är bara berörda för hantering av länkade listor med I/O-buffertar.</span><span class="sxs-lookup"><span data-stu-id="dba64-260">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="dba64-261">En lista med inmatade buffertar underhålls för paket som tas emot innan program varan är klar.</span><span class="sxs-lookup"><span data-stu-id="dba64-261">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="dba64-262">En lista över utdatacache bevaras för paket som skickas snabbare än maskin varu enheten kan hantera dem.</span><span class="sxs-lookup"><span data-stu-id="dba64-262">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="dba64-263">Bild 15 visar enkla indata och utdata länkade listor över data paket och de buffertar som utgör varje paket.</span><span class="sxs-lookup"><span data-stu-id="dba64-263">Figure 15 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

<span data-ttu-id="dba64-264">**Inmatad lista**</span><span class="sxs-lookup"><span data-stu-id="dba64-264">**Input List**</span></span>

![Inmatad lista](./media/user-guide/input-list.png)

<span data-ttu-id="dba64-266">**Lista över utdata**</span><span class="sxs-lookup"><span data-stu-id="dba64-266">**Output List**</span></span>

![Lista över utdata](./media/user-guide/output-list.png)

<span data-ttu-id="dba64-268">**FIGUR 15. Input-Output listor**</span><span class="sxs-lookup"><span data-stu-id="dba64-268">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="dba64-269">Program gränssnittet med buffrade driv rutiner med samma I/O-buffertar.</span><span class="sxs-lookup"><span data-stu-id="dba64-269">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="dba64-270">Vid överföring tillhandahåller program vara driv rutinen en eller flera buffertar som ska överföras.</span><span class="sxs-lookup"><span data-stu-id="dba64-270">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="dba64-271">När program varan begär indata returnerar driv rutinen indata i i/O-buffertar.</span><span class="sxs-lookup"><span data-stu-id="dba64-271">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="dba64-272">*I vissa program kan det vara praktiskt att bygga ett indatamängds gränssnitt för driv rutin som kräver att programmet utbyter en kostnads fri buffert för en buffert från driv rutinen. Detta kan under lätta vissa bearbetningar av buffertstorleken i driv rutinen.*</span><span class="sxs-lookup"><span data-stu-id="dba64-272">*In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver. This might alleviate some buffer allocation processing inside of the driver.*</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="dba64-273">Avbryt hantering</span><span class="sxs-lookup"><span data-stu-id="dba64-273">Interrupt Management</span></span>

<span data-ttu-id="dba64-274">I vissa program kan enhetens avbrotts frekvens förhindra skrivning av ISR i C eller att interagera med ThreadX på varje avbrott.</span><span class="sxs-lookup"><span data-stu-id="dba64-274">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX on each interrupt.</span></span> <span data-ttu-id="dba64-275">Om det till exempel tar 25us att spara och återställa den avbrutna kontexten är det inte lämpligt att utföra en fullständig kontext genom att spara om avbrotts frekvensen var 50uS.</span><span class="sxs-lookup"><span data-stu-id="dba64-275">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="dba64-276">I sådana fall används ett litet mängd-ISR för att hantera de flesta av enhetens avbrott.</span><span class="sxs-lookup"><span data-stu-id="dba64-276">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="dba64-277">Denna låga ISR-information skulle bara interagera med ThreadX vid behov.</span><span class="sxs-lookup"><span data-stu-id="dba64-277">This low-overhead ISR would only interact with ThreadX when necessary.</span></span>

<span data-ttu-id="dba64-278">En liknande diskussion finns i den avbrotts hanterings diskussionen i slutet av kapitel 3.</span><span class="sxs-lookup"><span data-stu-id="dba64-278">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="dba64-279">Tråd upphängning</span><span class="sxs-lookup"><span data-stu-id="dba64-279">Thread Suspension</span></span>

<span data-ttu-id="dba64-280">I exemplet på den enkla driv rutin som tidigare fanns i det här kapitlet, inaktive ras anroparen för Indataporten om ett kort inte är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="dba64-280">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="dba64-281">I vissa program kanske detta inte är acceptabelt.</span><span class="sxs-lookup"><span data-stu-id="dba64-281">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="dba64-282">Om till exempel tråden som ansvarar för bearbetning av indata från en driv rutin också har andra uppgifter, så kommer det förmodligen inte att gå att göra en inaktive ring av driv Rutinens indata.</span><span class="sxs-lookup"><span data-stu-id="dba64-282">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="dba64-283">I stället måste driv rutinen anpassas för bearbetning av begäran på samma sätt som andra bearbetnings begär Anden görs i tråden.</span><span class="sxs-lookup"><span data-stu-id="dba64-283">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="dba64-284">I de flesta fall placeras indatabufferten i en länkad lista och ett meddelande om inloggning skickas till trådens indatakö.</span><span class="sxs-lookup"><span data-stu-id="dba64-284">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread's input queue.</span></span>
