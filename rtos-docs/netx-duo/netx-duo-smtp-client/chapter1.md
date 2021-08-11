---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo SMTP-klient
description: SMTP Simple Mail Transfer Protocol (Smtp) är ett protokoll för överföring av e-post mellan nätverk och Internet.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: df8c6b6920577ebfc18ed9252761401c30822c034e30d7ae95b25778707f53d5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797831"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-smtp-client"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo SMTP-klient

SMTP Simple Mail Transfer Protocol (Smtp) är ett protokoll för överföring av e-post mellan nätverk och Internet. Den använder de tillförlitliga Transmission Control Protocol tjänster (TCP) för att utföra sin innehållsöverföringsfunktion.

## <a name="netx-duo-smtp-client-requirements"></a>NetX Duo SMTP-klientkrav

NetX Duo SMTP-klienten kräver att en NetX Duo IP-instans och En NetX Duo-paketpool skapas. SMTP-klienten använder en TCP-socket för att ansluta till en *SMTP-server på den välkända porten 25. Därför* måste TCP först aktiveras genom att anropa nx_tcp_enable *på* en TIDIGARE skapad IP-instans.

SMTP-klientens skapa-anrop (nxd_smtp_client_create) kräver en tidigare skapad paketpool för överföring av SMTP-kommandon till servern samt för att skicka det faktiska e-postmeddelandet. Paketnyttolasten beror på den förväntade storleken på e-postinnehållet och måste tillåta TCP, IP-huvud och MAC-huvud. (Observera att IPv6-huvudet är 40 byte medan IPv4-huvudet är 20 byte.)

Om hela e-postmeddelandet inte får plats i ett paket tilldelar SMTP-klienten ytterligare paket som ska innehålla resten av meddelandet.

## <a name="netx-duo-smtp-client-constraints"></a>Begränsningar för NetX Duo SMTP-klienten

Även om NetX Duo SMTP-protokollet implementerar standarderna RFC 2821 och 2554 finns det vissa begränsningar:

1. NetX Duo SMTP-klienten stöder endast LOGIN- och PLAIN-autentisering, men inte sammanfattad CRAM-MD5-autentisering.
2. NetX Duo SMTP-klientmeddelanden är begränsade till en mottagare per e-postobjekt och endast ett e-postmeddelande per TCP-anslutning med SMTP-servern.
3. ALTERNATIVEN VRFY, SEND, SOML, EXPN, SAML, ETRN, TURN och SIZE SMTP stöds inte.
4. SMTP-klienten är inte en e-postläsare ("e-postanvändaragent") som vanligtvis används för att skapa e-postmeddelandet. Det är bara en "e-postöverföringsagent". Den tillhandahåller nödvändig bearbetning av e-postmeddelandets brödtext för SMTP-transport som anges i RFC 2821. Den kontrollerar inte innehållet för rätt syntax, t.ex. mottagaren och den omvända vägen. Det finns ingen begränsning vad som finns i e-postbufferten, t.ex. MIME-data eller rensa sms. E-postmeddelandets format, som anges i RFC 2822 för att inkludera rubriker och meddelandetext, ligger utanför omfånget för SMTP-klient-API:et.

## <a name="commands-supported-by-netx-duo-smtp-client"></a>Kommandon som stöds av NetX Duo SMTP-klienten

NetX Duo SMTP-klienten använder följande kommandon under en e-postsession med en SMTP-server.

- **EHLO** Klienten vill initiera en session som innehåller vissa eller alla utökningsprotokoll SMTP-tjänster som är tillgängliga från SMTP-servern. Det här är standardinställningen.
- **HELO** Klienten vill initiera en session som är begränsad till grundläggande SMTP-tjänster.
- **E-POST** Klienten vill att servern ska ta emot klient-e-post.
- **AUTH** Klienten vill initiera autentisering av servern.
- **RCPT** Klienten vill skicka en postlåda till en annan värd som den vill att e-postmeddelandet ska levereras till.
- **DATA** Klienten vill initiera sändningen av e-postdata till servern.
- **AVSLUTA** Klienten vill avsluta sessionen.

## <a name="getting-started"></a>Komma igång

SMTP-klientprogrammet skapar en IP-instans och en aktiverar TCP på den IP-instansen. Därefter skapas SMTP-klienten med hjälp av följande tjänst:

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type,
    NXD_ADDRESS *server_address, UINT port);
```

Den *client_packet_pool_ptr* är en pekare till en tidigare skapad paketpool som SMTP-klienten använder för att skicka meddelanden till SMTP-servern.

Observera att ett program måste tillhandahålla en from_address *för* den lokala enheten och en server-IP-adress. Alla adresser måste vara fullständigt kvalificerade domännamn. Ett fullständigt kvalificerat domännamn innehåller en lokal del och ett domännamn, avgränsade med ett @-tecken. Observera att SMTP-klienten inte kontrollerar syntaxen *för from_address* eller *recipient_address* i nx_smtp_mail_send nedan.

När SMTP-klienten har skapats skapar SMTP-klientprogrammet ett e-postobjekt med ett korrekt formaterat SMTP-e-postmeddelande och skickar en begäran om e-postobjektet till SMTP-klienten med hjälp av följande API:

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address, UINT priority,
    CHAR *subject, CHAR *mail_body,
    UINT mail_body_length);
```

Det finns i princip ingen skillnad i att köra SMTP-klienten över IPv4 eller IPv6 ur användarperspektiv. Skillnader mellan de två IP-protokollen hanteras i det underliggande NetX Duo-lagret.

Observera att ett program som vill skicka e-post måste ange en mottagaradress i nx_smtp_client_mail samtalet. 

För autentisering kan användarnamn antingen vara fullständigt kvalificerade domännamn eller visa användarnamn. Detta beror på hur servern utför autentisering.

Demonstrationen i avsnittet Litet exempel senare i den här användarhandboken visar hur meddelandet ska formateras. Statusen om e-postobjektet har skickats kommer att NX_SUCCESS. Om ett fel inträffar, oavsett om det är ett internt fel, en bruten TCP-anslutning eller om du får en serversvarsfelkod, *nx_smtp_mail_send* returnerar felstatusen "inte noll".

När du skickar ett e-postobjekt skapar NetX Duo SMTP-klienten en ny TCP-anslutning med SMTP-servern och påbörjar en SMTP-session. I den här sessionen skickar klienten en serie kommandon till SMTP-servern som en del av SMTP-protokollet, vilket leder till att det faktiska e-postmeddelandet skickas. TCP-anslutningen avslutas sedan, oavsett resultatet av SMTP-sessionen.

Efter e-postöverföringen, oavsett om det lyckades eller misslyckades, returneras SMTP-klienten till det "ursprungliga" tillståndet och kan användas för en annan e-postöverföringssession.

## <a name="netx-duo-smtp-authentication"></a>NetX Duo SMTP-autentisering

Autentisering är ett sätt för SMTP-klienter att bevisa sin identitet för SMTP-servern och få sin e-post levererad som betrodda användare. De flesta kommersiella SMTP-servrar kräver att klienter autentiseras.

Autentiseringsdata består vanligtvis av avsändarens användarnamn och lösenord. Under en autentiseringsfråga frågar servern efter den här informationen och klienten svarar genom att skicka begärda data i kodat format. Servern avkodar data och försöker hitta en matchning i användardatabasen. Om det hittas anger servern att autentiseringen har lyckats. SMTP-autentisering definieras [i RFC 2554](http://www.ietf.org/rfc/rfc2554.txt).

Det finns två varianter av autentisering, *nämligen grundläggande* och *sammanfattande*. Sammanfattning stöds inte i den aktuella NetX Duo SMTP-klienten och beskrivs inte här. Grundläggande autentisering motsvarar det namn- och *lösenordsautentisering* som beskrivs ovan.  I grundläggande SMTP-autentisering är namn och lösenord base64-kodade. Fördelen med grundläggande autentisering är att det är enkelt att genomföra och använda den i stor omfattning. Den största nackdelen med grundläggande autentisering är namn och lösenordsdata överförs öppet i begäran.

### <a name="plain-authentication"></a>Vanlig autentisering

NetX Duo SMTP-klienten skickar ett AUTH-kommando med parametern PLAIN. Om NetX Duo SMTP-servern stöder den här typen av autentisering, svarar den med en 334-svarskod. Klienten svarar med ett enda base64-kodat användarnamn och lösenordsmeddelande till servern. Om servern fastställer att klientautentisering lyckas svarar den med 235-koden.

### <a name="login-authentication"></a>Inloggningsautentisering

NetX Duo SMTP-klienten skickar ett AUTH-kommando med parametern LOGIN. Om NetX Duo SMTP-servern stöder den här typen av autentisering, svarar den med en 334-svarskod som början på autentiseringsutmaningen. Den skickar en base64-kodad prompt tillbaka till klienten, som vanligtvis är "Användarnamn". Klienten avkodar prompten och svarar med ett base64-kodat användarnamn. Om servern accepterar klientens användarnamn skickar den en base64-kodad prompt för klientlösenordet. Klienten svarar med ett base64-kodat lösenord. Om servern fastställer att klientautentisering lyckas svarar den med 235-koden.

### <a name="no-authentication"></a>Ingen autentisering

Vissa SMTP-servrar konfigureras utan autentisering. I så fall visas inga autentiseringstyper i deras 250-svar på client BELO-meddelandet. Men inga autentiseringstyper i listan innebär inte nödvändigtvis att servern inte kräver eller stöder autentisering. Om klienten är konfigurerad för PLAIN- eller LOGIN-autentisering i den här situationen kommer NetX Duo Client-klienttrådaktiviteten som standard att vara PLAIN. Om Klienten har konfigurerats för NONE (Ingen) hoppas autentiseringssteget över och SMTP-tillståndet förs vidare till MAIL-tillståndet.

Observera att om klienten är konfigurerad för ingen autentisering och SMTP-servern stöder autentisering, växlas klientautentiseringstypen till PLAIN.

## <a name="rfcs-supported-by-netx-duo-smtp-client"></a>RFC:er som stöds av NetX Duo SMTP-klienten

NetX Duo SMTP-klient-API är kompatibelt med RFC2821 "Simple Mail Transfer Protocol" och RFC 2554 "SMTP-tjänsttillägg för autentisering. “
