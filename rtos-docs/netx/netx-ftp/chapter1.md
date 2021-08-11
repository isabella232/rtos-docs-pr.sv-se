---
title: Kapitel 1 – Introduktion till att Azure RTOS NetX FTP
description: FTP File Transfer Protocol (File Transfers) är ett protokoll som utformats för filöverföringar. FTP använder tillförlitliga Transmission Control Protocol tjänster (TCP) för att utföra sin filöverföringsfunktion.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 35a7487720578ce8da578c490d96aa3c444ee818167b1bbd10833556e34b3dce
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799480"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a>Kapitel 1 – Introduktion till att Azure RTOS NetX FTP

FTP File Transfer Protocol (File Transfers) är ett protokoll som utformats för filöverföringar. FTP använder tillförlitliga Transmission Control Protocol tjänster (TCP) för att utföra sin filöverföringsfunktion. Därför är FTP ett mycket tillförlitligt protokoll för filöverföring. FTP har också höga prestanda. Den faktiska FTP-filöverföringen utförs på en dedikerad FTP-anslutning.

## <a name="ftp-requirements"></a>FTP-krav

För att fungera korrekt kräver Azure RTOS NetX FTP-paketet att en NetX IP-instans redan har skapats. Dessutom måste TCP vara aktiverat på samma IP-instans. FTP-klientdelen av NetX FTP-paketet har inga ytterligare krav.

FTP-serverdelen av NetX FTP-paketet har flera ytterligare krav. För det första krävs fullständig åtkomst till DEN välkända *TCP-porten 21* för hantering av alla klient-FTP-kommandobegäranden och välkänd *port 20* för hantering av alla klient-FTP-dataöverföringar. FTP-servern är också utformad för användning med filex-inbäddat filsystem. Om FileX inte är tillgängligt kan användaren porta de delar av FileX som används i deras egen miljö. Detta beskrivs i senare avsnitt i den här guiden.

## <a name="ftp-constraints"></a>FTP-begränsningar

FTP-standarden har många alternativ för representation av fildata. Precis som Unix-implementeringar förutsätter NetX FTP följande begränsningar i filformatet:

- Filtyp: **Binär**
- Filformat: **Endast icke-utskrivet**
- Filstruktur: **Endast filstruktur**
- Överföringsläge: **Endast strömläge**

## <a name="ftp-file-names"></a>FTP-filnamn

FTP-filnamn ska ha formatet för målfilsystemet (vanligtvis FileX). De bör vara NULL-avslutade ASCII-strängar, med fullständig sökvägsinformation om det behövs. Det finns ingen angiven gräns för storleken på FTP-filnamn i NetX FTP-implementeringen. Paketpoolens nyttolaststorlek bör dock kunna hantera den maximala sökvägen och/eller filnamnet.

## <a name="ftp-client-commands"></a>FTP-klientkommandon

FTP har en enkel mekanism för att öppna anslutningar och utföra fil- och katalogåtgärder. Det finns i princip en uppsättning vanliga FTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den välkända *TCP-porten 21.* Nedan visas några av de grundläggande FTP-kommandona:

### <a name="ftp-command-and-meaning"></a>FTP-kommando och betydelse

- **CWD-sökväg:** *Ändra arbetskatalog*
- **DELE-filnamn:** *Ta bort angivet filnamn*
- **LIST-katalog:** *Hämta kataloglista*
- **MKD-katalog:** *Skapa ny katalog*
- **NLST-katalog:** *Hämta kataloglista*
- **NOOP:** *Ingen åtgärd, returnerar lyckad*
- **PASS-lösenord:** *Ange lösenord för inloggning*
- **PASV:** *Begär passivt överföringsläge*
- **PWD-sökväg:** *Upphämtning av aktuell katalogsökväg*
- **QUIT**: *Avsluta klientanslutningen*
- **RETR-filnamn:** *Läsa angiven fil*
- **RMD-katalog:** *Ta bort angiven katalog*
- **RNFR oldfilename: Ange den** *fil som ska byta namn*
- **RNTO newfilename:** *Byt namn på filen till det angivna filnamnet*
- **STOR-filnamn:** *Skriv angiven fil*
- **TYP I:** Välj *bild av binär fil*
- **ANVÄNDARNAMN:** *Ange användarnamn för inloggning*
- **PORT ip_address,port:** *Ange IP-adress och Klientdataport*

Dessa ASCII-kommandon används internt av NetX FTP-klientprogrammet för att utföra FTP-åtgärder med FTP-servern.

## <a name="ftp-server-responses"></a>FTP-serversvar

FTP-servern använder den välkända *TCP-porten 21 för att* ange klientkommandobegäranden. När FTP-servern bearbetar klientkommandot returneras ett 3-siffrigt numeriskt svar i ASCII följt av en valfri ASCII-sträng. Det numeriska svaret används av FTP-klientprogrammet för att avgöra om åtgärden lyckades eller misslyckades. Följande listar olika FTP-serversvar på klientkommandon:

### <a name="first-numeric-field-and-meaning"></a>Första numeriska fält och betydelse

- **1xx:** *Positiv preliminär status – ett annat svar kommer*.
- **2xx:** *Positiv slutförandestatus*.
- **3xx:** *Positiv preliminär status – ett annat kommando måste skickas*.
- **4xx:** *Tillfälligt feltillstånd*.
- **5xx:** *Felvillkor.*

### <a name="second-numeric-field-and-meaning"></a>Andra numeriska fält och betydelse

- **x0x:** Syntaxfel i kommandot.
- **x1x:** Informationsmeddelande.
- **x2x:** Anslutningsrelaterat.
- **x3x:** Autentiseringsrelaterad.
- **x4x:** Ospecificerad.
- **x5x:** Relaterat filsystem.

En klientbegäran om att koppla från en FTP-anslutning med kommandot QUIT besvaras vanligtvis med en "221"-kod från servern – om frånkopplingen lyckas.

## <a name="ftp-passive-transfer-mode"></a>FTP-passivt överföringsläge

Som standard använder NetX FTP-klienten det aktiva transportläget för att utbyta data via datasocketen med FTP-servern. Problemet med det här arrangemanget är att ftp-klienten måste öppna en TCP-serversocket för att FTP-servern ska kunna ansluta till. Detta representerar en möjlig säkerhetsrisk och kan blockeras av klientbrandväggen. Passivt överföringsläge skiljer sig från aktivt transportläge genom att FTP-servern skapar TCP-serversocketen på dataanslutningen. Detta eliminerar säkerhetsrisken (för FTP-klienten).

För att aktivera passiv dataöverföring anropar programmet *nx_ftp_client_passive_mode_set* på en tidigare skapad FTP-klient med det andra argumentet inställt på NX_TRUE. Därefter görs alla efterföljande NetX FTP-klienttjänster för överföring av data (NLST, RETR, STOR) i passivt transportläge.

FTP-klienten skickar först PASV-kommandot (inga argument). Om FTP-servern stöder den här begäran returneras svaret 227 "OK". Klienten skickar sedan begäran, t.ex. RETR. Om servern nekar passivt överföringsläge returnerar NetX FTP-klienttjänsten en felstatus.

Om du vill inaktivera passivt transportläge och återgå till aktivt transportläge anropar *programmet nx_ftp_client_passive_mode_set* med det andra argumentet inställt på NX_FALSE.

## <a name="ftp-communication"></a>FTP-kommunikation

FTP-servern använder den välkända *TCP-porten 21 för att* ange klientbegäranden. FTP-klienter kan använda alla tillgängliga TCP-portar. Den allmänna sekvensen för FTP-händelser är följande:

### <a name="ftp-read-file-requests"></a>FTP-läsfilsbegäranden

1. Klientproblem TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar svaret "230" för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar svaret "200" för att signalera att det lyckades.
1. Klienten skickar "PORT"-meddelande med IP-adress och port.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. Klienten skickar ett RETR-meddelande med filnamn att läsa.
1. Server skapar datasocket och ansluter med klientdataporten som anges i kommandot "PORT".
1. Servern skickar svaret "125" till signalfilen som lästs har startat.
1. Servern skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar servern från dataanslutningen.
1. Servern skickar "250"-svar för att signalfilläsningen lyckas.
1. Klienter skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

Som tidigare nämnts är den enda skillnaden mellan FTP som körs via IPv4 och IPv6 att KOMMANDOT PORT ersätts med EPRT-kommandot för IPv6

Om FTP-klienten gör en läsbegäran i läget för passiv överföring är kommandosekvensen följande **(** fetstilta rader anger ett annat steg än aktivt överföringsläge):

1. Klienten har problem med TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar "230"-svar för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. **Klienten skickar ETT PASV-meddelande.**
1. **Servern skickar "227"-svar och IP-adress och port som klienten ska ansluta till för att signalera att det lyckades.**
1. Klienten skickar ett RETR-meddelande med filnamn att läsa.
1. **Server skapar dataserversocket och lyssnar efter klientanslutningsbegäran på den här socketen med den port som anges i svaret "227".**
1. **Servern skickar "150"-svar på kontrollsocketen för att signalera att filläsningen har startat.**
1. Servern skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar servern från dataanslutningen.
1. **Servern skickar "226"-svar på kontrollsocketen för att signalera att filläsningen lyckas.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

### <a name="ftp-write-requests"></a>FTP-skrivbegäranden

1. Klienten har problem med TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar "230"-svar för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. Klienten skickar "PORT"-meddelande med IP-adress och port.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. Klienten skickar meddelandet "STOR" med filnamnet att skriva.
1. Server skapar datasocket och ansluter med klientdataporten som anges i kommandot "PORT".
1. Servern skickar svaret "125" för att signalera att filskrivningen har startat.
1. Klienten skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar klienten från dataanslutningen.
1. Servern skickar "250"-svar för att signalfilskrivningen lyckas.
1. Klienter skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

Om FTP-klienten gör en skrivbegäran i läget för passiv överföring är kommandosekvensen följande **(** fetstilta rader anger ett annat steg än aktivt överföringsläge):

1. Klienten har problem med TCP-anslutning till serverport 21.
1. Servern skickar svaret "220" för att signalera att det lyckades.
1. Klienten skickar meddelandet "USER" med "username".
1. Servern skickar svaret "331" för att signalera att det lyckades.
1. Klienten skickar "PASS"-meddelande med "lösenord".
1. Servern skickar "230"-svar för att signalera att det lyckades.
1. Klienten skickar ett "TYPE I"-meddelande för binär överföring.
1. Servern skickar "200"-svar för att signalera att det lyckades.
1. **Klienten skickar ETT PASV-meddelande.**
1. **Servern skickar "227"-svar och IP-adress och port som klienten ska ansluta till för att signalera att det lyckades.**
1. Klienten skickar meddelandet "STOR" med filnamnet att skriva.
1. **Server skapar dataserversocket och lyssnar efter klientanslutningsbegäran på den här socketen med den port som anges i svaret "227".**
1. **Servern skickar "150"-svar på kontrollsocketen för att signalera att filskrivningen har startat.**
1. Klienten skickar innehållet i filen via dataanslutningen. Den här processen fortsätter tills filen har överförts helt.
1. När du är klar kopplar klienten från dataanslutningen.
1. **Servern skickar "226"-svar på kontrollsocketen för att signalera att filskrivningen lyckas.**
1. Klienten skickar "QUIT" för att avsluta FTP-anslutningen.
1. Servern skickar svaret "221" för att signalera att frånkopplingen lyckas.
1. Servern kopplar från FTP-anslutningen.

## <a name="ftp-authentication"></a>FTP-autentisering

När en FTP-anslutning sker måste klienten ange ett användarnamn *och* lösenord för *servern.* Vissa FTP-platser tillåter det som kallas *anonym FTP*, som tillåter FTP-åtkomst utan ett specifikt användarnamn och lösenord. För den här typen av anslutning ska "anonym" anges som användarnamn och lösenordet ska vara en fullständig e-postadress.

Användaren ansvarar för att tillhandahålla NetX FTP med inloggnings- och utloggningsautentiseringsrutiner. Dessa anges under funktionen ***nx_ftp_server_create** _ och anropas från lösenordsbearbetningen. Om funktionen _login* returnerar NX_SUCCESS autentiseras anslutningen och FTP-åtgärder tillåts. Om inloggningsfunktionen *returnerar* något annat än NX_SUCCESS avvisas anslutningsförsöket.

## <a name="ftp-multi-thread-support"></a>FTP-stöd för flera trådar

NetX FTP-klienttjänsterna kan anropas från flera trådar samtidigt. Läs- eller skrivbegäranden för en viss FTP-klientinstans bör dock göras i följd från samma tråd.

## <a name="ftp-rfcs"></a>FTP-RFC

NetX FTP är kompatibel med RFC959 och relaterade RFC: er.