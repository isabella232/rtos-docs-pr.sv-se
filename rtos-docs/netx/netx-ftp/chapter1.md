---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX FTP
description: FTP (File Transfer Protocol) är ett protokoll som är utformat för fil överföringar. FTP använder Reliable Transmission Control Protocol-tjänster (TCP) för att utföra sin fil överförings funktion.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86e132daf96f9039631234f10c8e239b61ad5126
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826733"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX FTP

FTP (File Transfer Protocol) är ett protokoll som är utformat för fil överföringar. FTP använder Reliable Transmission Control Protocol-tjänster (TCP) för att utföra sin fil överförings funktion. Därför är FTP ett mycket tillförlitligt fil överförings protokoll. FTP är också hög prestanda. Den faktiska FTP-filöverföringen utförs på en dedikerad FTP-anslutning.

## <a name="ftp-requirements"></a>FTP-krav

För att kunna fungera korrekt måste en NetX-återställnings tider redan ha skapats av Azure NetX FTP-paketet. Dessutom måste TCP vara aktiverat på samma IP-instans. FTP-klienttjänsten i NetX FTP-paketet har inga ytterligare krav.

FTP-server delen av FTP-paketet NetX har flera ytterligare krav. Först måste du ha fullständig åtkomst till den *välkända TCP-porten 21* för att hantera alla KLIENTERs FTP-kommandon och *välkända port 20* för hantering av alla klient-FTP-dataöverföringar. FTP-servern är också avsedd att användas med det inbäddade fil systemet FileX. Om FileX inte är tillgängligt kan användaren hamna i de delar av FileX som används i sin egen miljö. Detta beskrivs i senare avsnitt i den här hand boken.

## <a name="ftp-constraints"></a>FTP-begränsningar

FTP-standarden har många alternativ för åter givning av fildata. I likhet med UNIX-implementeringar antar NetX FTP följande fil formats begränsningar:

- Filtyp: **binär**
- Fil format: **endast icke-skriva ut**
- Fil struktur: **endast fil struktur**
- Överförings läge: **endast ström läge**

## <a name="ftp-file-names"></a>FTP-filnamn

FTP-filnamn ska vara i formatet för mål fil systemet (vanligt vis FileX). De ska vara NULL-terminerade ASCII-strängar, med fullständig Sök vägs information vid behov. Det finns ingen angiven gräns för storleken på FTP-filnamn i FTP-implementeringen NetX. Paket poolens nytto Last storlek bör dock kunna hantera den maximala sökvägen och/eller fil namnet.

## <a name="ftp-client-commands"></a>Kommandon för FTP-klient

FTP har en enkel mekanism för att öppna anslutningar och utföra fil-och katalog åtgärder. Det finns i princip en uppsättning standard-FTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den *välkända TCP-porten 21*. Nedan visas några av de grundläggande FTP-kommandona:

### <a name="ftp-command-and-meaning"></a>FTP-kommando och betydelse

- **CWD sökväg**: *ändra arbets katalog*
- **&-Fil** namn: *ta bort det angivna fil namnet*
- **List katalog**: *Hämta katalog lista*
- **MKD-katalog**: *Skapa ny katalog*
- **NLST katalog**: *Hämta katalog lista*
- **Noop**: *Ingen åtgärd, returnerar lyckade*
- Lösen **ord**: *Ange lösen ord för inloggning*
- **Pasv**: *begär passivt överförings läge*
- **PWD-sökväg**: *pickup aktuell katalog Sök väg*
- **Avsluta**: *Avsluta klient anslutning*
- **Retr fil namn**: *Läs angiven fil*
- **RMD-katalog**: *ta bort angiven katalog*
- **RNFR oldfilename**: *Ange fil att byta namn på*
- **RNTO newfilename**: *Byt namn på filen till det angivna fil namnet*
- **Lagr fil namn**: *Skriv angiven fil*
- **Skriv I**: *Välj avbildning av binär fil*
- **Användar namn**: *Ange användar namn för inloggning*
- **Port ip_address, Port**: *Ange IP-adress och klient data port*

Dessa ASCII-kommandon används internt av NetX FTP-klientprogrammet för att utföra FTP-åtgärder med FTP-servern.

## <a name="ftp-server-responses"></a>Svar på FTP-servern

FTP-servern använder sig av en *VÄLKÄND TCP-port 21* för att fält begär Anden om klient kommandon. När FTP-servern bearbetar klient kommandot returneras ett fyrsiffrigt numeriskt svar i ASCII följt av en valfri ASCII-sträng. Det numeriska svaret används av FTP-klientprogramvaran för att avgöra om åtgärden lyckades eller misslyckades. Här följer en lista över olika FTP-servrars svar på klient kommandon:

### <a name="first-numeric-field-and-meaning"></a>Första numeriska fältet och innebörden

- **1xx**: *positiv preliminär status – ett annat svar kommer*.
- **2xx**: *positiv slut för ande status*.
- **3xx**: *positiv preliminär status – ett annat kommando måste skickas*.
- **4xx**: *tillfälligt fel tillstånd*.
- **5xx**: *fel villkor.*

### <a name="second-numeric-field-and-meaning"></a>Andra numeriska fältet och betydelsen

- **X0X**: syntaxfel i kommandot.
- **x1x**: informations meddelande.
- **x2x**: anslutning relaterad.
- **x3x**: autentisering relaterad.
- **x4x**: ospecificerad.
- **x5x**: fil system relaterat.

Till exempel kommer en klientbegäran att koppla från en FTP-anslutning med kommandot QUIT att svara med en "221"-kod från servern – om från kopplingen lyckas.

## <a name="ftp-passive-transfer-mode"></a>Läge för passiv FTP-överföring

Som standard använder FTP-klienten för NetX det aktiva transport läget för att utbyta data via datasocketen med FTP-servern. Problemet med den här överenskommelsen är att det krävs att FTP-klienten öppnar en TCP-servers socket för att FTP-servern ska kunna ansluta till den. Detta innebär en möjlig säkerhets risk och kan blockeras av klient brand väggen. Passivt överförings läge skiljer sig från aktivt transport läge genom att låta FTP-servern skapa TCP-serverns socket på data anslutningen. Detta eliminerar säkerhets risken (för FTP-klienten).

Om du vill aktivera passiv data överföring anropar programmet *nx_ftp_client_passive_mode_set* på en tidigare skapad FTP-klient med det andra argumentet inställt på NX_TRUE. Därefter försöker alla efterföljande NetX FTP-klienter för överföring av data (NLST, RETR, lagr) i passivt transport läge.

FTP-klienten skickar först kommandot PASV (inga argument). Om FTP-servern har stöd för denna begäran returnerar den 227 "OK"-svaret. Klienten skickar sedan begäran till RETR. Om servern vägrar passivt överförings läge returnerar NetX FTP-klienttjänsten en fel status.

Om du vill inaktivera passivt transport läge och återgå till aktivt transport läge, anropar programmet *nx_ftp_client_passive_mode_set* med det andra argumentet inställt på NX_FALSE.

## <a name="ftp-communication"></a>FTP-kommunikation

FTP-servern använder sig av en *VÄLKÄND TCP-port 21* för att fält klient begär Anden. FTP-klienter kan använda alla tillgängliga TCP-portar. Den allmänna sekvensen av FTP-händelser är följande:

### <a name="ftp-read-file-requests"></a>Begäran om läsning av FTP-fil

1. Klient problem TCP Anslut till server port 21.
1. Servern skickar "220"-svar till signalen lyckades.
1. Klienten skickar meddelandet "användare" med "username."
1. Servern skickar "331"-svar till signalen lyckades.
1. Klienten skickar "PASS"-meddelandet med "Password".
1. Servern skickar "230"-svar till signalen lyckades.
1. Klienten skickar meddelandet "typ I" för binär överföring.
1. Servern skickar "200"-svar till signalen lyckades.
1. Klienten skickar meddelandet "PORT" med IP-adress och port.
1. Servern skickar "200"-svar till signalen lyckades.
1. Klienten skickar meddelandet "RETR" med fil namnet att läsa.
1. Servern skapar datasocket och ansluter med den klient data port som anges i "PORT"-kommandot.
1. Servern skickar "125"-svaret till signal filen Read har startats.
1. Servern skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar servern från data anslutningen.
1. Servern skickar "250"-svaret till signal filen Read har slutförts.
1. Klienter skickar "avsluta" för att avsluta FTP-anslutningen.
1. Servern skickar "221"-svaret till signal-från koppling lyckades.
1. Servern kopplar från FTP-anslutningen.

Som tidigare nämnts är den enda skillnaden mellan FTP som körs via IPv4 och IPv6 att PORT kommandot ersätts med kommandot EPRT för IPv6

Om FTP-klienten gör en läsbegäran i passivt överförings läge är kommando ordningen enligt följande (**fetstilta** linjer indikerar ett annat steg från aktivt överförings läge):

1. Klient problem TCP Anslut till server port 21.
1. Servern skickar "220"-svar till signalen lyckades.
1. Klienten skickar meddelandet "användare" med "username."
1. Servern skickar "331"-svar till signalen lyckades.
1. Klienten skickar "PASS"-meddelandet med "Password".
1. Servern skickar "230"-svar till signalen lyckades.
1. Klienten skickar meddelandet "typ I" för binär överföring.
1. Servern skickar "200"-svar till signalen lyckades.
1. **Klienten skickar meddelandet "PASV".**
1. **Servern skickar "227"-svar, och IP-adressen och porten som klienten ska ansluta till, för att signalera lyckas.**
1. Klienten skickar meddelandet "RETR" med fil namnet att läsa.
1. **Servern skapar dataserver-socket och lyssnar efter klient anslutnings förfrågan på denna socket med den port som anges i svaret "227".**
1. **Servern skickar "150"-svaret på kontrollens socket till signal filens läsning har påbörjats.**
1. Servern skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar servern från data anslutningen.
1. **Servern skickar "226"-svaret på kontroll-socketen till signal filens läsning har slutförts.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar "221"-svaret till signal-från koppling lyckades.
1. Servern kopplar från FTP-anslutningen.

### <a name="ftp-write-requests"></a>FTP-Write-begäranden

1. Klient problem TCP Anslut till server port 21.
1. Servern skickar "220"-svar till signalen lyckades.
1. Klienten skickar meddelandet "användare" med "username."
1. Servern skickar "331"-svar till signalen lyckades.
1. Klienten skickar "PASS"-meddelandet med "Password".
1. Servern skickar "230"-svar till signalen lyckades.
1. Klienten skickar meddelandet "typ I" för binär överföring.
1. Servern skickar "200"-svar till signalen lyckades.
1. Klienten skickar meddelandet "PORT" med IP-adress och port.
1. Servern skickar "200"-svar till signalen lyckades.
1. Klienten skickar meddelandet "lagr" med fil namnet att skriva.
1. Servern skapar datasocket och ansluter med den klient data port som anges i "PORT"-kommandot.
1. Servern skickar "125"-svar till signal filen som skrivs har startats.
1. Klienten skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar klienten från data anslutningen.
1. Servern skickar "250"-svar till signal filens skrivning har slutförts.
1. Klienter skickar "avsluta" för att avsluta FTP-anslutningen.
1. Servern skickar "221"-svaret till signal-från koppling lyckades.
1. Servern kopplar från FTP-anslutningen.

Om FTP-klienten gör en skrivbegäran i passivt överförings läge är kommando ordningen enligt följande (**fetstilta** rader visar ett annat steg från aktivt överförings läge):

1. Klient problem TCP Anslut till server port 21.
1. Servern skickar "220"-svar till signalen lyckades.
1. Klienten skickar meddelandet "användare" med "username."
1. Servern skickar "331"-svar till signalen lyckades.
1. Klienten skickar "PASS"-meddelandet med "Password".
1. Servern skickar "230"-svar till signalen lyckades.
1. Klienten skickar meddelandet "typ I" för binär överföring.
1. Servern skickar "200"-svar till signalen lyckades.
1. **Klienten skickar meddelandet "PASV".**
1. **Servern skickar "227"-svar, och IP-adressen och porten som klienten ska ansluta till, för att signalera lyckas.**
1. Klienten skickar meddelandet "lagr" med fil namnet att skriva.
1. **Servern skapar dataserver-socket och lyssnar efter klient anslutnings förfrågan på denna socket med den port som anges i svaret "227".**
1. **Servern skickar "150"-svaret på kontroll-socketen till signal fils skrivning har startats.**
1. Klienten skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar klienten från data anslutningen.
1. **Servern skickar "226"-svar på kontroll-socketen till signal fils skrivningen lyckades.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar "221"-svaret till signal-från koppling lyckades.
1. Servern kopplar från FTP-anslutningen.

## <a name="ftp-authentication"></a>FTP-autentisering

När en FTP-anslutning sker måste klienten förse servern med ett *användar namn* och *lösen ord*. Vissa FTP-platser tillåter vad som kallas *Anonym FTP*, vilket tillåter FTP-åtkomst utan ett visst användar namn och lösen ord. För den här typen av anslutning ska "Anonym" anges för användar namn och lösen ordet ska vara en fullständig e-postadress.

Användaren ansvarar för att tillhandahålla NetX FTP med inloggnings-och utloggnings rutiner för autentisering. De anges under ***nx_ftp_server_create** _-funktionen och anropas från lösen ords bearbetningen. Om funktionen _login * returnerar NX_SUCCESS, är anslutningen autentiserad och FTP-åtgärder tillåts. Om *inloggnings* funktionen annars returnerar något annat än NX_SUCCESS avvisas anslutnings försöket.

## <a name="ftp-multi-thread-support"></a>Stöd för FTP multi-Thread

NetX FTP Client Services kan anropas från flera trådar samtidigt. Läs-eller Skriv begär Anden för en viss FTP-serverinstans bör dock göras i följd från samma tråd.

## <a name="ftp-rfcs"></a>FTP RFC

NetX FTP är kompatibel med RFC959 och relaterade RFC: er.