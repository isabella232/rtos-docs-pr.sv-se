---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo TFTP
description: Tftp Trivial File Transfer Protocol (The Trivial File Transfer Protocol) är ett enkelt protokoll som utformats för filöverföringar.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4854f96d8f230d7c1f21700ac731d6430854a950009d3ed51fbf90d37885f255
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791983"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo TFTP 

Tftp Trivial File Transfer Protocol (The Trivial File Transfer Protocol) är ett enkelt protokoll som utformats för filöverföringar. Till skillnad från mer robusta protokoll utför TFTP inte omfattande felkontroller och kan också ha begränsad prestanda eftersom det är ett stopp- och vänteprotokoll. När ett TFTP-datapaket har skickats väntar avsändaren på att ett ACK ska returneras av mottagaren. Även om detta är enkelt begränsar det övergripande TFTP-dataflödet. TFTP-paketet gör att värdar kan använda TFTP-protokollet via IP-nätverk.

## <a name="tftp-requirements"></a>TFTP-krav

För att tftp-klienterna ska fungera korrekt i NetX Duo TFTP-paketet måste en IP-instans redan ha skapats. Dessutom måste UDP vara aktiverat på samma IP-instans. Klientdelen av NetX Duo TFTP-paketet har inga ytterligare krav.

TFTP-serverdelen av NetX Duo TFTP-paketet har flera ytterligare krav. För det första krävs fullständig åtkomst till UDP:s *välkända port 69 för* hantering av alla TFTP-klientbegäranden. TFTP-servern är också utformad för användning med filex-inbäddat filsystem. Om FileX inte är tillgängligt kan användaren porta de delar av FileX som används i deras egen miljö. Detta beskrivs i senare avsnitt i den här guiden.

## <a name="tftp-file-names"></a>TFTP-filnamn 

TFTP-filnamn ska vara i formatet för målfilsystemet. De bör vara NULL-avslutade ASCII-strängar, med fullständig sökvägsinformation om det behövs. Det finns ingen angiven gräns för storleken på TFTP-filnamn i NetX Duo TFTP-implementeringen.

## <a name="tftp-messages"></a>TFTP-meddelanden

TFTP har en mycket enkel mekanism för att öppna, läsa, skriva och stänga filer. Det finns i princip 2–4 byte TFTP-rubrik under UDP-rubriken. Definitionen av öppna TFTP-filmeddelanden har följande format:

**hhf... f0OCTET0**

Plats:

- **fältet** 2 byte Opcode  
0x0001 -> Open för läsning  
0x0002 -> Open för skrivning

- **f... f** n-byte filnamnsfält

- NULL-avslutningstecken på 1 byte

- **OKTETT** ASCII "OCTET" för att ange binär överföring

- NULL-avslutningstecken på 1 byte

Definitionen av TFTP-skriv-, ACK- och felmeddelandena skiljer sig något åt och definieras på följande sätt:

**lobbbbbd... D**

Plats:

- **fältet** 2 byte Opcode  
0x0003 -> datapaket  
0x0004 -> ACK för senaste läsning  
0x0005 -> feltillstånd  

- **bbbb** 2-bytes blocknummerfält (1-n)

- **d... d** n-byte datafält


- 0x0001 (läst) Filnamn 0 OKTETT 0

- 0x0002 (skrivning) Filnamn 0 OKTETT 0

## <a name="tftp-communication"></a>TFTP-kommunikation

TFTP-servrar använder den välkända UDP-port 69 för att lyssna efter klientbegäranden. TFTP-klientsocketar kan bindas till alla tillgängliga UDP-portar. Datapaketnyttolasten som innehåller filen som ska laddas upp eller ned skickas i 512 byte-segment tills det sista paketet som innehåller < 512 byte. Därför signalerar ett paket som innehåller färre än 512 byte slutet på filen. Den allmänna händelsesekvensen är följande:

TFTP-läsfilbegäranden:

1.  Klienten skickar en "Open For Read"-begäran med filnamnet och väntar på ett svar från servern.

2.  Servern skickar de första 512 bytena i filen eller mindre om filstorleken är mindre än 512 byte.

3.  Klienten tar emot data, skickar en ACK och väntar på nästa paket från servern för filer som innehåller mer än 512 byte.

4.  Sekvensen avslutas när klienten tar emot ett paket som innehåller mindre än 512 byte.

TFTP-skrivbegäranden:

1.  Klienten skickar en "Open for Write"-begäran med filnamnet och väntar på en ACK med blocknumret 0 från servern.

2.  När servern är redo att skriva filen skickar den ett ACK med blocknumret noll.

3.  Klienten skickar de första 512 bytena av filen (eller mindre för filer som är mindre än 512 byte) till servern och väntar på en ACK tillbaka.

4.  Servern skickar en ACK när byte har skrivits.

5.  Sekvensen avslutas när klienten har skrivit ett paket som innehåller färre än 512 byte.
 

## <a name="tftp-server-session-timer"></a>TFTP-serversessionstimer

TFTP-servern har ett begränsat antal platser för klientbegäran. Om en klientsession verkar ha tagits bort kan det facket inte vara tillgängligt för återanvändning. Men om NX_TFTP_SERVER_RETRANSMIT_ENABLE är aktiverat skapar NetX Duo TFTP-servern en sessionstimer som övervakar tidsgränsen för var och en av dess klientsessioner. När tidsgränsen för en session upphör att gälla avslutas den och alla öppna filer stängs. Därför blir "platsen" tillgänglig för en annan TFTP-klientbegäran.

Om du vill ange tidsgränsen justerar du konfigurationsalternativet NX_TFTP_SERVER_RETRANSMIT_TIMEOUT som standard är 200 timer tick. Intervallet mellan vilka tidsgränser för sessioner kontrolleras anges av NX_TFTP_SERVER_TIMEOUT_PERIOD som är 20 timer tick som standard.

När TFTP-klienten har laddat upp (skrivit) filer till TFTP FileX-mediet måste mediet tömmas så att data kan skrivas från TFTP-serverns RAM-disk till det underliggande mediet (TFTP-klientens diskminne). Detta kan göras med hjälp fx_media_flush tjänsten om programmet inte vill stänga TFTP-servern.

När TFTP-servern har stängts bör programmet, om det inte har någon ytterligare användning för FileX-mediet, sedan stänga med hjälp av fx_media_close tjänsten. Detta rensar fildata tillbaka till TFTP-klientdisken, stänger öppna filer och uppdaterar kataloginformationen till mediet.

Avsnittet "Litet exempel" i det här kapitlet visar detta.

Ett tredje alternativ för att uppdatera FileX-media är att kompilera FileX-biblioteket med FX_FAULT_TOLERANT eller FX_FAULT_TOLERANT_DATA istället för att använda FileX-tjänster explicit. Om det här definieras skickar FileX automatiskt skrivbegäranden till mediedrivrutinen. De här alternativen kan begränsa prestandan men ger bättre skydd mot förlorade fildata eller förlorade kluster. Mer information om detta och FileX i allmänhet finns i användarhandboken för Express Logic FileX.

## <a name="tftp-multi-thread-support"></a>TFTP-stöd för flera trådar

NetX Duo TFTP-klienttjänsterna kan anropas från flera trådar samtidigt. Läs- eller skrivbegäranden för en viss TFTP-klientinstans bör dock göras i följd från samma tråd.

## <a name="tftp-rfcs"></a>TFTP-RFC:er

NetX Duo TFTP är kompatibelt med RFC1350 och relaterade RFC: er.

