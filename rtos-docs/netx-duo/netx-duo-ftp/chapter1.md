---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo FTP
description: FTP (File Transfer Protocol) är ett protokoll som är utformat för fil överföringar.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d56b20b1c7d719d1b7d9c8c5b2fe234d5577da3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825986"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ftp"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo FTP

FTP (File Transfer Protocol) är ett protokoll som är utformat för fil överföringar. FTP använder Reliable Transmission Control Protocol-tjänster (TCP) för att utföra sin fil överförings funktion. Därför är FTP ett mycket tillförlitligt fil överförings protokoll. FTP är också hög prestanda. Den faktiska FTP-filöverföringen utförs på en dedikerad FTP-anslutning. NetX Duo FTP rymmer både IPv4-och IPv6-nätverk. IPv6 ändrar inte FTP-protokollet direkt, även om vissa ändringar i det ursprungliga NetX FTP API är nödvändiga för att hantera IPv6 och beskrivs i det här dokumentet.

## <a name="ftp-requirements"></a>FTP-krav

NetX FTP-paketet kräver NetX Duo för att fungera korrekt. Värd programmet måste skapa en IP-instans för att köra NetX-tjänster och periodiska uppgifter. Om du kör FTP-värdprogram över ett IPv6-nätverk måste IPv6 och ICMPv6 vara aktiverat för IP-aktiviteten. TCP måste också aktive ras för antingen IPv6-eller IPv4-nätverk. IPv6-värd programmet måste ange dess LINKLOCAL och globala IPv6-adress med hjälp av IPv6 API och/eller DHCPv6. Ett demo program i avsnittet "litet exempel system" i **kapitel 2** visar hur detta görs.

FTP-servern och klienten är också utformade för att fungera med det inbäddade fil systemet FileX. Om FileX inte är tillgängligt kan värd utvecklaren implementera eller ersätta sitt eget fil system längs rikt linjerna som föreslås i filex_stub. h genom att definiera var och en av de tjänster som anges i filen. Detta beskrivs i senare avsnitt i den här hand boken.

FTP-klienttjänsten i NetX FTP-paketet har inga ytterligare krav.

FTP-server delen av FTP-paketet NetX har flera ytterligare krav. Först måste du ha fullständig åtkomst till den *välkända TCP-porten 21* för att hantera alla KLIENTERs FTP-kommandon och *välkända port 20* för hantering av alla klient-FTP-dataöverföringar.

## <a name="ftp-constraints"></a>FTP-begränsningar

FTP-standarden har många alternativ för åter givning av fildata. NetX FTP implementerar inte växel alternativ, t. ex. ls – Al. NetX FTP-server förväntar sig att ta emot begär Anden och deras argument i ett enda paket i stället för efterföljande paket.

I likhet med UNIX-implementeringar antar NetX FTP följande fil formats begränsningar:

- Filtyp: **binär**
- Fil format: **endast icke-skriva ut**
- Fil struktur: **endast fil struktur**

## <a name="ftp-file-names"></a>FTP-filnamn

FTP-filnamn ska vara i formatet för mål fil systemet (vanligt vis FileX). De ska vara NULL-terminerade ASCII-strängar, med fullständig Sök vägs information vid behov. Det finns ingen angiven gräns för storleken på FTP-filnamn i FTP-implementeringen NetX. Paket poolens nytto Last storlek bör dock kunna hantera den maximala sökvägen och/eller fil namnet.

## <a name="ftp-client-commands"></a>Kommandon för FTP-klient

FTP har en enkel mekanism för att öppna anslutningar och utföra fil-och katalog åtgärder. Det finns i princip en uppsättning standard-FTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den *välkända TCP-porten 21*. Nedan visas några av de grundläggande FTP-kommandona. Observera att den enda skillnaden när FTP körs över IPv6 är att PORT kommandot ersätts med kommandot EPRT:

- CWD-sökväg *ändra arbets katalog*
- & fil namn *ta bort det angivna fil namnet*
- EPRT ip_address, Port *Ange IPv6-adress och klient data port*
- EPSV *begär passivt överförings läge för IPv6*
- Visa lista över katalogen *Hämta katalog*
- MKD Directory *Skapa ny katalog*
- NLST Directory *Hämta katalog lista*
- NOOP *Ingen åtgärd, returnerar lyckade*
- Lösen ord *för att ange lösen ord för inloggning*
- PASV *begär passivt överförings läge för IPv4*
- PORT ip_address, Port *Ange IP-adress och klient data port*
- PWD-sökväg *pickup aktuell katalog Sök väg*
- Avsluta *Avsluta klient anslutning*
- RETR fil namn *läsa angiven fil*
- RMD katalog *ta bort angiven katalog*
- RNFR oldfilename *Ange fil att byta namn* på
- RNTO newfilename *Byt namn på filen till det angivna fil namnet*
- LAGR fil namn *Skriv angiven fil*
- TYP I *Välj binär fil avbildning*
- ANVÄNDAR användar namn *Ange användar namn för inloggning*

Dessa ASCII-kommandon används internt av NetX FTP-klientprogrammet för att utföra FTP-åtgärder med FTP-servern.

## <a name="ftp-server-responses"></a>Svar på FTP-servern

När FTP-servern bearbetar klientbegäran returneras ett tredimensionellt svar i ASCII följt av valfri ASCII-text. Det numeriska svaret används av FTP-klientprogramvaran för att avgöra om åtgärden lyckades eller misslyckades. I följande lista visas olika svar på FTP-servern för klient begär Anden:

**Första numeriska fält betydelse**

- 1xx *positiv preliminär status – ett annat svar kommer*.
- status för 2xx- *positiv slut för ande*.
- 3xx *positiv preliminär status – ett annat kommando måste skickas*.
- 4xx *tillfälligt fel tillstånd*.
- *fel tillstånd* för 5xx.

**Betydelse för andra numeriska fält**

- X0X- *syntaxfel i kommandot*.
- *informations meddelande* för x1x.
- x2x- *anslutning relaterad*.
- x3x- *autentisering är relaterad*.
- x4x har inte *angetts*.
- x5x *fil system relaterat*.

Till exempel kommer en klientbegäran att koppla från en FTP-anslutning med kommandot QUIT att svara med en "221"-kod från servern – om från kopplingen lyckas.

## <a name="ftp-passive-transfer-mode"></a>Läge för passiv FTP-överföring

Som standard använder NetX Duo FTP-klienten det aktiva transport läget för att utbyta data över datasocketen med FTP-servern. Problemet med den här överenskommelsen är att det krävs att FTP-klienten öppnar en TCP-servers socket för att FTP-servern ska kunna ansluta till den. Detta innebär en möjlig säkerhets risk och kan blockeras av klient brand väggen. Passivt överförings läge skiljer sig från aktivt transport läge genom att låta FTP-servern skapa TCP-serverns socket på data anslutningen. Detta eliminerar säkerhets risken (för FTP-klienten).

Om du vill aktivera passiv data överföring anropar programmet *nx_ftp_client_passive_mode_set* på en tidigare skapad FTP-klient med det andra argumentet inställt på NX_TRUE. Därefter försöker alla efterföljande NetX Duo FTP client-tjänster för överföring av data (NLST, RETR, lagr) i passivt transport läge.

FTP-klienten skickar först kommandot passivt (inga argument), kommandot PASV för IPv4-eller EPSV-kommandot för IPv6. Om FTP-servern har stöd för den här begäran returnerar den 227 "OK"-svaret för PASV, och 229 "OK"-svar för EPSV. Klienten skickar sedan begäran till RETR. Om servern vägrar passivt överförings läge returnerar tjänsten NetX Duo FTP client en fel status.

Om du vill inaktivera passivt transport läge och återgå till aktivt transport läge, anropar programmet *nx_ftp_client_passive_mode_set* med det andra argumentet inställt på NX_FALSE.

## <a name="ftp-communication"></a>FTP-kommunikation

FTP-servern använder sig av en *VÄLKÄND TCP-port 21* för att fält klient begär Anden. FTP-klienter kan använda alla tillgängliga TCP-portar. Den allmänna sekvensen av FTP-händelser är följande:

**Begäran om läsning av FTP-fil**:

1. Klient problem TCP Anslut till server port 21.
1. Servern skickar "220"-svar till signalen lyckades.
1. Klienten skickar meddelandet "användare" med "username."
1. Servern skickar "331"-svar till signalen lyckades.
1. Klienten skickar "PASS"-meddelandet med "Password".
1. Servern skickar "230"-svar till signalen lyckades.
1. Klienten skickar meddelandet "typ I" för binär överföring.
1. Servern skickar "200"-svar till signalen lyckades.
1. *IPv4-program*: klienten skickar meddelandet "Port" med IP-adress och port.<br />*IPv6-program*: klienten skickar meddelandet "EPRT" med IP-adress och port.
1. Servern skickar "200"-svar till signalen lyckades.
1. Klienten skickar meddelandet "RETR" med fil namnet att läsa.
1. Servern skapar datasocket och ansluter med den klient data port som anges i "PORT"-kommandot.
1. Servern skickar "125"-svaret till signal filen Read har startats.
1. Servern skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar servern från data anslutningen.
1. Servern skickar "250"-svaret till signal filen Read har slutförts.
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar "221"-svaret till signal-från koppling lyckades.
1. Servern kopplar från FTP-anslutningen.

Som tidigare nämnts, är den enda skillnaden mellan FTP som körs via IPv4 och

IPv6 är PORT kommandot ersatt med kommandot EPRT för IPv6

Om FTP-klienten gör en läsbegäran i passivt överförings läge är kommando ordningen enligt följande (**fetstilta** linjer indikerar ett annat steg från aktivt överförings läge):

1. Klient problem TCP Anslut till server port 21.
1. Servern skickar "220"-svar till signalen lyckades.
1. Klienten skickar meddelandet "användare" med "username."
1. Servern skickar "331"-svar till signalen lyckades.
1. Klienten skickar "PASS"-meddelandet med "Password".
1. Servern skickar "230"-svar till signalen lyckades.
1. Klienten skickar meddelandet "typ I" för binär överföring.
1. Servern skickar "200"-svar till signalen lyckades.
1. ***IPv4-program:* Klienten skickar meddelandet "PASV".**<br />**_IPv6-program:_ Klienten skickar meddelandet "EPSV".**
1. ***IPv4-program:* Servern skickar "227"-svar, och IP-adressen och porten som klienten ska ansluta till, för att signalera lyckas.**<br />**_IPv6-program:_ Servern skickar "229"-svar, och IP-adressen och porten som klienten ska ansluta till, för att signalera lyckas.**
1. Klienten skickar meddelandet "RETR" med fil namnet att läsa.
1. **Servern skapar dataserver-socket och lyssnar efter klient anslutnings förfrågan på denna socket med den port som anges i svaret i steg 10.**
1. **Servern skickar "150"-svaret på kontrollens socket till signal filens läsning har påbörjats.**
1. Servern skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar servern från data anslutningen.
1. **Servern skickar "226"-svaret på kontroll-socketen till signal filens läsning har slutförts.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar "221"-svaret till signal-från koppling lyckades.
1. Servern kopplar från FTP-anslutningen.

**FTP-Write-begär Anden**:

1. Klient problem TCP Anslut till server port 21.
1. Servern skickar "220"-svar till signalen lyckades.
1. Klienten skickar meddelandet "användare" med "username."
1. Servern skickar "331"-svar till signalen lyckades.
1. Klienten skickar "PASS"-meddelandet med "Password".
1. Servern skickar "230"-svar till signalen lyckades.
1. Klienten skickar meddelandet "typ I" för binär överföring.
1. Servern skickar "200"-svar till signalen lyckades.
1. *IPv4-program*: klienten skickar meddelandet "Port" med IP-adress och port.<br />*IPv6-program*: klienten skickar meddelandet "EPRT" med IP-adress och port.
1. Servern skickar "200"-svar till signalen lyckades.
1. Klienten skickar meddelandet "lagr" med fil namnet att skriva.
1. Servern skapar datasocket och ansluter med den klient data port som anges i föregående "EPRT"-eller "PORT"-kommando.
1. Servern skickar "125"-svar till signal filen som skrivs har startats.
1. Klienten skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar klienten från data anslutningen.
1. Servern skickar "250"-svar till signal filens skrivning har slutförts.
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
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
1. ***IPv4-program:* Klienten skickar meddelandet "PASV".**<br />**_IPv6-program:_ Klienten skickar meddelandet "EPSV".**
1. ***IPv4-program:* Servern skickar "227"-svar, och IP-adressen och porten som klienten ska ansluta till, för att signalera lyckas.**<br />**_IPv6-program:_ Servern skickar "229"-svar, och IP-adressen och porten som klienten ska ansluta till, för att signalera lyckas.**
1. Klienten skickar meddelandet "lagr" med fil namnet att skriva.
1. **Servern skapar dataserver-socket och lyssnar efter klient anslutnings förfrågan på denna socket med den port som anges i svaret i steg 10.**
1. **Servern skickar "150"-svaret på kontroll-socketen till signal fils skrivning har startats.**
1. Klienten skickar innehållet i filen via data anslutningen. Den här processen fortsätter tills filen har överförts fullständigt.
1. När det är klart kopplar klienten från data anslutningen.
1. **Servern skickar "226"-svar på kontroll-socketen till signal fils skrivningen lyckades.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar "221"-svaret till signal-från koppling lyckades.
1. Servern kopplar från FTP-anslutningen.

## <a name="ftp-authentication"></a>FTP-autentisering

När en FTP-anslutning sker måste klienten förse servern med ett *användar namn* och *lösen ord*. Vissa FTP-platser tillåter vad som kallas *Anonym FTP*, vilket tillåter FTP-åtkomst utan ett visst användar namn och lösen ord. För den här typen av anslutning ska "Anonym" anges för användar namn och lösen ordet ska vara en fullständig e-postadress.

Användaren ansvarar för att tillhandahålla NetX FTP med inloggnings-och utloggnings rutiner för autentisering. De anges under ***nxd_ftp_server_create** _ och _*_nx_ftp_server_create_*_ tjänster och anropas från lösen ords bearbetningen. Skillnaden mellan de två är att den _*_nxd_ftp_server_create_*_ ingångs funktions pekare till inloggning och utloggning autentisera funktioner förväntar sig _*_NXD_ADDRESS_*_ för netx Duo-adressen. Den här data typen innehåller både IPv4-eller IPv6-adress format, vilket gör att den här funktionen "Duo" stöder både IPv4-och IPv6-nätverk. De _ *_nx_ftp_server_create_** ingångs funktions pekare till inloggning och utloggning autentisera funktioner förväntar sig ulong IP-typ. Den här funktionen är begränsad till IPv4-nätverk. Utvecklaren uppmanas att använda "Duo"-tjänsten närhelst det är möjligt.

Om funktionen *login* returnerar NX_SUCCESS, är anslutningen autentiserad och FTP-åtgärder tillåts. Om *inloggnings* funktionen annars returnerar något annat än NX_SUCCESS avvisas anslutnings försöket.

## <a name="ftp-multi-thread-support"></a>Stöd för FTP multi-Thread

NetX FTP Client Services kan anropas från flera trådar samtidigt. Läs-eller Skriv begär Anden för en viss FTP-serverinstans bör dock göras i följd från samma tråd.

## <a name="ftp-rfcs"></a>FTP RFC

NetX Duo FTP är kompatibel med RFC 959, RFC 2428 och relaterade RFC: er.
