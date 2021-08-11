---
title: Kapitel 1 – Introduktion till att Azure RTOS NetX Duo FTP
description: Ftp File Transfer Protocol (The File Transfer Protocol) är ett protokoll som utformats för filöverföringar.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a36357ce486d5ba8a68b23c829de6c4b821dfb3cc62f47b0958ff32deaa2f7a7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791303"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ftp"></a>Kapitel 1 – Introduktion till att Azure RTOS NetX Duo FTP

Ftp File Transfer Protocol (The File Transfer Protocol) är ett protokoll som utformats för filöverföringar. FTP använder tillförlitliga Transmission Control Protocol (TCP) för att utföra filöverföringsfunktionen. Därför är FTP ett mycket tillförlitligt filöverföringsprotokoll. FTP har också höga prestanda. Den faktiska FTP-filöverföringen utförs på en dedikerad FTP-anslutning. NetX Duo FTP kan hantera både IPv4- och IPv6-nätverk. IPv6 ändrar inte FTP-protokollet direkt, även om vissa ändringar i det ursprungliga NetX FTP-API:et är nödvändiga för att hantera IPv6 och beskrivs i det här dokumentet.

## <a name="ftp-requirements"></a>FTP-krav

NetX FTP-paketet kräver NetX Duo för att fungera korrekt. Värdprogrammet måste skapa en IP-instans för att köra NetX-tjänster och periodiska uppgifter. Om du kör FTP-värdprogrammet via ett IPv6-nätverk måste IPv6 och ICMPv6 vara aktiverade för IP-uppgiften. TCP måste också vara aktiverat för Antingen IPv6- eller IPv4-nätverk. IPv6-värdprogrammet måste ange sin länklokala och globala IPv6-adress med hjälp av IPv6-API:et och/eller DHCPv6. Ett demoprogram i avsnittet "Litet exempelsystem" **i kapitel 2** visar hur detta görs.

FTP-servern och -klienten är också utformade för att fungera med filex-inbäddat filsystem. Om FileX inte är tillgängligt kan värdutvecklaren implementera eller ersätta sitt eget filsystem enligt de riktlinjer som föreslås i filex_stub.h genom att definiera var och en av de tjänster som anges i filen. Detta beskrivs i senare avsnitt i den här guiden.

FTP-klientdelen av NetX FTP-paketet har inga ytterligare krav.

FTP-serverdelen av NetX FTP-paketet har flera ytterligare krav. För det första krävs fullständig åtkomst till TCP *välkänd port 21* för hantering av alla klient-FTP-kommandobegäranden och välkänd port 20 för hantering av alla klient-FTP-dataöverföringar. 

## <a name="ftp-constraints"></a>FTP-begränsningar

FTP-standarden har många alternativ för representation av fildata. NetX FTP implementerar inte växelalternativ, t.ex. ls –al. NetX FTP-servern förväntar sig att ta emot begäranden och deras argument i ett enda paket i stället för på varandra följande paket.

Precis som UNIX implementeringar förutsätter NetX FTP följande begränsningar i filformatet:

- Filtyp: **Binär**
- Filformat: **Endast icke-utskrivet**
- Filstruktur: **Endast filstruktur**

## <a name="ftp-file-names"></a>FTP-filnamn

FTP-filnamn ska ha formatet för målfilsystemet (vanligtvis FileX). De bör vara NULL-avslutade ASCII-strängar, med fullständig sökvägsinformation om det behövs. Det finns ingen angiven gräns för storleken på FTP-filnamn i NetX FTP-implementeringen. Paketpoolens nyttolaststorlek bör dock kunna hantera den maximala sökvägen och/eller filnamnet.

## <a name="ftp-client-commands"></a>FTP-klientkommandon

FTP har en enkel mekanism för att öppna anslutningar och utföra fil- och katalogåtgärder. Det finns i princip en uppsättning vanliga FTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den välkända *TCP-porten 21.* Nedan visas några av de grundläggande FTP-kommandona. Observera att den enda skillnaden när FTP körs över IPv6 är att KOMMANDOT PORT ersätts med EPRT-kommandot:

- CWD-sökväg *Ändra arbetskatalog*
- DELE-filnamn Ta *bort angivet filnamn*
- EPRT ip_address, port *Ange IPv6-adress och Klientdataport*
- EPSV *Begär passivt överföringsläge för IPv6*
- LIST-katalog *Hämta kataloglista*
- MKD-katalog *Skapa ny katalog*
- NLST-katalog *Hämta kataloglista*
- NOOP *Ingen åtgärd, returnerar lyckad*
- PASS-lösenord *Ange lösenord för inloggning*
- PASV *Begär passivt överföringsläge för IPv4*
- PORT ip_address,port *Ange IP-adress och Klientdataport*
- PWD-sökväg *Upphämtning av aktuell katalogsökväg*
- AVSLUTA *Avsluta klientanslutning*
- RETR-filnamn *Läs angiven fil*
- RMD-katalog *Ta bort angiven katalog*
- RNFR oldfilename Ange fil *att byta namn på*
- RNTO newfilename *Byt namn på fil till det angivna filnamnet*
- STOR-filnamn *Skriv angiven fil*
- BILD AV TYPEN I *Välj binär fil*
- ANVÄNDARNAMN Ange *användarnamn för inloggning*

Dessa ASCII-kommandon används internt av NetX FTP-klientprogrammet för att utföra FTP-åtgärder med FTP-servern.

## <a name="ftp-server-responses"></a>FTP-serversvar

När FTP-servern bearbetar klientbegäran returnerar den ett 3-siffrigt kodat svar i ASCII följt av valfri ASCII-text. Det numeriska svaret används av FTP-klientprogrammet för att avgöra om åtgärden lyckades eller misslyckades. I följande lista visas olika FTP-serversvar på klientbegäranden:

**Första betydelse för numeriska fält**

- 1xx *Positiv preliminär status – ett annat svar kommer*.
- 2xx *Positiv slutförandestatus*.
- 3xx *Positiv preliminär status – ett annat kommando måste skickas*.
- 4xx *Tillfälligt feltillstånd*.
- 5xx *Felvillkor.*

**Andra numeriska fält som betyder**

- x0x *Syntax-fel i kommandot*.
- x1x *Informational message*.
- *x2x-anslutning relaterad*.
- *x3x-autentiseringsrelaterad*.
- x4x *Ospecificerad*.
- *x5x-filsystem som är relaterat till*.

Till exempel kommer en klientbegäran om att koppla från en FTP-anslutning med kommandot QUIT vanligtvis att besvaras med en "221"-kod från servern – om frånkopplingen lyckas.

## <a name="ftp-passive-transfer-mode"></a>FTP-passivt överföringsläge

Som standard använder NetX Duo FTP-klienten det aktiva transportläget för att utbyta data via datasocketen med FTP-servern. Problemet med detta är att FTP-klienten måste öppna en TCP-serversocket för att FTP-servern ska kunna ansluta till. Detta representerar en möjlig säkerhetsrisk och kan blockeras av klientbrandväggen. Läget för passiv överföring skiljer sig från aktivt transportläge genom att FTP-servern skapar TCP-serversocketen på dataanslutningen. Detta eliminerar säkerhetsrisken (för FTP-klienten).

För att aktivera passiv dataöverföring anropar programmet *nx_ftp_client_passive_mode_set* på en tidigare skapad FTP-klient med det andra argumentet inställt på NX_TRUE. Därefter görs alla efterföljande NetX Duo FTP-klienttjänster för överföring av data (NLST, RETR, STOR) i passivt transportläge.

FTP-klienten skickar först det passiva kommandot (inga argument), PASV-kommandot för IPv4- eller EPSV-kommandot för IPv6. Om FTP-servern stöder den här begäran returneras 227 "OK"-svaret för PASV och 229 "OK"-svar för EPSV. Klienten skickar sedan begäran, t.ex. RETR. Om servern nekar passivt överföringsläge returnerar NetX Duo FTP-klienttjänsten en felstatus.

Om du vill inaktivera passivt transportläge och återgå till aktivt transportläge anropar *programmet nx_ftp_client_passive_mode_set* med det andra argumentet inställt på NX_FALSE.

## <a name="ftp-communication"></a>FTP-kommunikation

FTP-servern använder den välkända *TCP-porten 21 till* fältet Klientbegäranden. FTP-klienter kan använda alla tillgängliga TCP-portar. Den allmänna sekvensen med FTP-händelser är följande:

**FTP-läsfilbegäranden:**

1. Klienten har problem med TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar svaret "230" för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. *IPv4-program:* Klienten skickar "PORT"-meddelande med IP-adress och port.<br />*IPv6-program:* Klienten skickar "EPRT"-meddelande med IP-adress och port.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. Klienten skickar ETT RETR-meddelande med filnamn att läsa.
1. Server skapar datasocket och ansluter med klientdataporten som anges i kommandot "PORT".
1. Servern skickar svaret "125" till signalfilen som lästs har startat.
1. Servern skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar servern från dataanslutningen.
1. Servern skickar "250"-svar för att signalfilläsningen lyckas.
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

Som tidigare nämnts är den enda skillnaden mellan FTP som körs över IPv4 och

IPv6 är portkommandot ersätts med EPRT-kommandot för IPv6

Om FTP-klienten gör en läsbegäran i läget för passiv överföring är kommandosekvensen följande **(** fetstilta rader anger ett annat steg än aktivt överföringsläge):

1. Klienten har problem med TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar svaret "230" för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. ***IPv4-program:* Klienten skickar ETT PASV-meddelande.**<br />**_IPv6-program:_ Klienten skickar ett EPSV-meddelande.**
1. ***IPv4-program:* Servern skickar "227"-svar och IP-adress och port som klienten ska ansluta till för att signalera att det lyckades.**<br />**_IPv6-program:_ Servern skickar "229"-svar och IP-adress och port som klienten ska ansluta till för att signalera att det lyckades.**
1. Klienten skickar ETT RETR-meddelande med filnamn att läsa.
1. **Server skapar dataserversocket och lyssnar efter klientanslutningsbegäran på den här socketen med den port som anges i svaret i steg 10.**
1. **Servern skickar "150"-svar på kontrollsocketen för att signalera att filläsningen har startat.**
1. Servern skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar servern från dataanslutningen.
1. **Servern skickar "226"-svar på kontrollsocketen för att signalera att filläsningen lyckas.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

**FTP-skrivbegäranden:**

1. Klienten har problem med TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar svaret "230" för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. *IPv4-program:* Klienten skickar "PORT"-meddelande med IP-adress och port.<br />*IPv6-program:* Klienten skickar "EPRT"-meddelande med IP-adress och port.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. Klienten skickar meddelandet "STOR" med filnamnet att skriva.
1. Server skapar datasocket och ansluter med klientdataporten som angavs i föregående "EPRT" eller "PORT"-kommando.
1. Servern skickar svaret "125" för att signalera att filskrivningen har startat.
1. Klienten skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar klienten från dataanslutningen.
1. Servern skickar "250"-svar för att signalfilskrivningen lyckas.
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

Om FTP-klienten gör en skrivbegäran i läget för passiv överföring är kommandosekvensen följande **(** fetstilta rader anger ett annat steg än aktivt överföringsläge):

1. Klienten har problem med TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar svaret "230" för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. ***IPv4-program:* Klienten skickar ETT PASV-meddelande.**<br />**_IPv6-program:_ Klienten skickar ett EPSV-meddelande.**
1. ***IPv4-program:* Servern skickar "227"-svar och IP-adress och port som klienten ska ansluta till för att signalera att det lyckades.**<br />**_IPv6-program:_ Servern skickar "229"-svar och IP-adress och port som klienten ska ansluta till för att signalera att det lyckades.**
1. Klienten skickar meddelandet "STOR" med filnamnet att skriva.
1. **Server skapar dataserversocket och lyssnar efter klientanslutningsbegäran på den här socketen med den port som anges i svaret i steg 10.**
1. **Servern skickar "150"-svar på kontrollsocketen för att signalera att filskrivningen har startat.**
1. Klienten skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar klienten från dataanslutningen.
1. **Servern skickar "226"-svar på kontrollsocketen för att signalera att filskrivningen lyckas.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

## <a name="ftp-authentication"></a>FTP-autentisering

När en FTP-anslutning sker måste klienten ange ett användarnamn *och* lösenord för *servern.* Vissa FTP-platser tillåter det som kallas *anonym FTP*, som tillåter FTP-åtkomst utan ett specifikt användarnamn och lösenord. För den här typen av anslutning ska "anonym" anges som användarnamn och lösenordet ska vara en fullständig e-postadress.

Användaren ansvarar för att tillhandahålla NetX FTP med inloggnings- och utloggningsautentiseringsrutiner. Dessa tillhandahålls under ***nxd_ftp_server_create** _ och _*_nx_ftp_server_create_*_ tjänster och anropas från lösenordsbearbetningen. Skillnaden mellan de två är _*_pekare nxd_ftp_server_create_*_ indatafunktionen för att logga in och logga ut autentisera funktioner förväntar sig NetX Duo-adresstypen _*_NXD_ADDRESS_*_. Den här datatypen innehåller både IPv4- eller IPv6-adressformat, vilket gör att den här funktionen är "duo"-tjänsten som stöder både IPv4- och IPv6-nätverk. Funktionen _ nx_ftp_server_create **_pekare_* för inloggning och utloggning autentisera funktioner förväntar sig ULONG IP-adresstyp. Den här funktionen är begränsad till IPv4-nätverk. Utvecklaren uppmanas att använda "duo"-tjänsten när det är möjligt.

Om *inloggningsfunktionen* returnerar NX_SUCCESS autentiseras anslutningen och FTP-åtgärder tillåts. Om inloggningsfunktionen *annars returnerar* något annat än NX_SUCCESS, avvisas anslutningsförsöket.

## <a name="ftp-multi-thread-support"></a>FTP-stöd för flera trådar

NetX FTP-klienttjänsterna kan anropas från flera trådar samtidigt. Läs- eller skrivbegäranden för en viss FTP-klientinstans bör dock göras i följd från samma tråd.

## <a name="ftp-rfcs"></a>FTP-RFC:er

NetX Duo FTP är kompatibel med RFC 959, RFC 2428 och relaterade RFC: er.
