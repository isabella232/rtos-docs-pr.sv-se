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
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo TFTP 

Trivial File Transfer Protocol (TFTP) är ett Lightweight-protokoll som är utformat för fil överföringar. Till skillnad från robusta protokoll utför TFTP inte en omfattande fel kontroll och kan också ha begränsad prestanda eftersom det är ett stopp-och-wait-protokoll. När ett TFTP-datapaket har skickats väntar avsändaren tills en bekräftelse skickas tillbaka av mottagaren. Även om detta är enkelt begränsar det det övergripande TFTP-dataflödet. Med TFTP-paketet kan värdar använda TFTP-protokollet över IP-nätverk.

## <a name="tftp-requirements"></a>TFTP-krav

För att fungera korrekt kräver TFTP-klienter i NetX Duo-paketet att en IP-instans redan har skapats. Dessutom måste UDP vara aktiverat på samma IP-instans. Klient delen av NetX Duo TFTP-paketet har inga ytterligare krav.

TFTP-server delen av NetX Duo TFTP-paketet har flera ytterligare krav. Först måste du ha fullständig åtkomst till den UDP- *välkända porten 69* för att hantera alla förfrågningar om klient-TFTP. TFTP-servern är också avsedd att användas med det inbäddade fil systemet FileX. Om FileX inte är tillgängligt kan användaren hamna i de delar av FileX som används i sin egen miljö. Detta beskrivs i senare avsnitt i den här hand boken.

## <a name="tftp-file-names"></a>TFTP-filnamn 

TFTP-filnamn ska vara i formatet för mål fil systemet. De ska vara NULL-terminerade ASCII-strängar, med fullständig Sök vägs information vid behov. Det finns ingen angiven gräns i storleken på TFTP-filnamn i NetX Duo TFTP-implementeringen.

## <a name="tftp-messages"></a>TFTP-meddelanden

TFTP har en väldigt enkel mekanism för att öppna, läsa, skriva och stänga filer. Det finns i princip 2-4 byte i TFTP-huvudet under UDP-huvudet. Definitionen av TFTP-filen öppna meddelanden har följande format:

**oooof... f0OCTET0**

Plats:

- **Oooo** 2 – byte opcode-fält  
0x0001-> öppen för läsning  
0x0002-> öppna för skrivning

- **f...** fält för f-byte-filnamn

- 0 1 – byte NULL avslutnings Character

- **Oktett** ASCII "OKTETT" för att ange binär överföring

- 0 1 – byte NULL avslutnings Character

Definitionen av TFTP Write-, ACK-och fel meddelanden skiljer sig något från varandra och definieras enligt följande:

**oooobbbbd... styr**

Plats:

- **Oooo** 2 – byte opcode-fält  
0x0003-> data paket  
0x0004 – > ACK för senaste läsning  
0x0005 – fel villkor för >  

- **bbbb** 2-byte block Number (1-n)

- **d...** data fält för d n-byte


- 0x0001 (Läs) fil namn 0 OKTETT 0

- 0x0002 (Skriv) fil namn 0 OKTETT 0

## <a name="tftp-communication"></a>TFTP-kommunikation

TFTP-servrar använder välkända UDP-port 69 för att lyssna efter klient förfrågningar. TFTP-klientens Sockets kan bindas till valfri tillgänglig UDP-port. Data paketets nytto last som innehåller filen som ska laddas upp eller hämtas skickas i 512 byte-segment tills det sista paketet som innehåller < 512 byte. Ett paket som innehåller färre än 512 byte signalerar därför slutet av filen. Den allmänna sekvensen av händelser är följande:

TFTP-Läs fil begär Anden:

1.  Klienten utfärdar en "öppen för läsning"-begäran med fil namnet och väntar på ett svar från servern.

2.  Servern skickar den första 512 byten av filen eller mindre om fil storleken är mindre än 512 byte.

3.  Klienten tar emot data, skickar en bekräftelse och väntar på nästa paket från servern för filer som innehåller mer än 512 byte.

4.  Sekvensen slutar när klienten tar emot ett paket som innehåller färre än 512 byte.

TFTP-Skriv begär Anden:

1.  Klienten utfärdar en "öppen för skrivning"-begäran med fil namnet och väntar på en bekräftelse med block antalet 0 från servern.

2.  När servern är redo att skriva filen skickas en bekräftelse med ett block antal noll.

3.  Klienten skickar de första 512 byten av filen (eller mindre för filer som är mindre än 512 byte) till servern och väntar på en ACK tillbaka.

4.  Servern skickar en ACK efter att byte har skrivits.

5.  Sekvensen slutar när klienten har skrivit ett paket som innehåller färre än 512 byte.
 

## <a name="tftp-server-session-timer"></a>Timer för TFTP-serversessionen

TFTP-servern har ett begränsat antal klient begär ande platser. Om en klientsession verkar släppas, kan den platsen inte vara tillgänglig för åter användning. Om NX_TFTP_SERVER_RETRANSMIT_ENABLE alternativet är aktive rad skapar dock NetX Duo TFTP-servern en session-timer som övervakar tids gränsen för var och en av dess klientsessioner. När tids gränsen för sessionen upphör att gälla avslutas den och alla öppna filer stängs. Facket blir därför tillgängligt för en annan TFTP-klientbegäran.

Om du vill ange tids gränsen justerar du konfigurations alternativet NX_TFTP_SERVER_RETRANSMIT_TIMEOUT som som standard är 200 timer-Tick. Intervallet mellan vilka sessions-timeout-värden kontrol leras anges av NX_TFTP_SERVER_TIMEOUT_PERIOD som är 20 timer-Tick som standard.

När TFTP-klienten har laddat upp (skrivna) filer till TFTP FileX-mediet, måste mediet rensas så att data kan skrivas från TFTP-serverns RAM-disk till det underliggande mediet (TFTP-klientens disk minne). Detta kan göras med hjälp av fx_media_flush tjänsten om programmet inte vill stänga TFTP-servern.

Men när du har stängt TFTP-servern bör programmet, om det inte har någon annan användning för FileX-mediet, stänga mediet med hjälp av tjänsten fx_media_close. Detta tömmer fil data tillbaka till TFTP-klientdatorn, stänger öppna filer och uppdaterar katalog informationen till mediet.

Avsnittet "små exempel" i det här kapitlet visar detta.

Ett tredje alternativ för att uppdatera FileX-mediet är att kompilera FileX-biblioteket med FX_FAULT_TOLERANT eller FX_FAULT_TOLERANT_DATA alternativ i stället för att använda FileX-tjänster explicit. Om det har definierats skickar FileX automatiskt Skriv förfrågningar till medie driv rutinen. De här alternativen kan begränsa prestanda men ger bättre skydd mot förlorade fildata eller förlorade kluster. Mer information om detta och FileX i allmänhet finns i användar handboken för Express Logic FileX.

## <a name="tftp-multi-thread-support"></a>Stöd för TFTP-flera trådar

Klient tjänsterna NetX Duo TFTP kan anropas från flera trådar samtidigt. Läs-eller Skriv begär Anden för en viss TFTP-serverinstans bör dock göras i följd från samma tråd.

## <a name="tftp-rfcs"></a>TFTP-rapporter

NetX Duo TFTP är kompatibelt med RFC1350 och relaterade RFC: er.

