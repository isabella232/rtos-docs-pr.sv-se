---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SMTP client
description: Simple Mail Transfer Protocol (SMTP) är ett protokoll för att överföra e-post mellan nätverk och Internet.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f58a0c235f5c2cd108ba97afe676ffa9b66e715c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825794"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-smtp-client"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SMTP client

Simple Mail Transfer Protocol (SMTP) är ett protokoll för att överföra e-post mellan nätverk och Internet. Den använder sig av pålitliga Transmission Control Protocol-tjänster (TCP) för att utföra sin innehålls överförings funktion.

## <a name="netx-duo-smtp-client-requirements"></a>NetX Duo SMTP-klient krav

NetX Duo SMTP-klienten måste skapa en NetX Duo-IP-instans och NetX Duo-adresspoolen. SMTP-klienten använder en TCP-socket för att ansluta till en SMTP-server på den *välkända port 25. Därför* måste TCP först aktive ras genom att anropa tjänsten *nx_tcp_enable* på en tidigare skapad IP-instans.

SMTP-klienten för att skapa samtal (nxd_smtp_client_create) kräver en tidigare skapad modempool för överföring av SMTP-kommandon till servern samt för att skicka det faktiska e-postmeddelandet. Paketets nytto Last beror på den förväntade storleken på e-postinnehållet och måste tillåta TCP, IP-huvud och MAC-huvud. (Observera att IPv6-huvudet är 40 byte när IPv4-rubriken är 20 byte.)

Om hela e-postmeddelandet inte får plats i ett paket, allokerar SMTP-klienten ytterligare paket som innehåller resten av meddelandet.

## <a name="netx-duo-smtp-client-constraints"></a>NetX Duo SMTP-klient begränsningar

Även om NetX Duo SMTP-protokollet implementerar RFC 2821-och 2554-standarder finns det vissa begränsningar:

1. NetX Duo SMTP-klienten stöder bara inloggning och enkel autentisering, men inte CRAM-MD5 Digest-autentisering.
2. NetX Duo SMTP-klientcertifikaten är begränsade till en mottagare per e-postobjekt och bara ett e-postmeddelande per TCP-anslutning med SMTP-servern.
3. VRFY, SEND, SOML, EXPN, SAML, ETRN, TURN och SIZE SMTP-alternativ stöds inte.
4. SMTP-klienten är inte e-postwebbläsare ("Mail user agent") som vanligt vis används för att skapa e-postmeddelandet. Det är endast en "e-postöverförings agent". Det ger den nödvändiga bearbetningen av e-postmeddelandets brödtext för SMTP-transport enligt vad som anges i RFC 2821. Det kontrollerar inte innehållet för korrekt syntax, t. ex. mottagare och omvänd väg. Det finns ingen begränsning vad finns i e-postbufferten, t. ex. MIME-data eller rensa textmeddelanden. E-postmeddelandet format, som anges i RFC 2822 för inkludering av rubriker och meddelande text ligger utanför omfånget för SMTP-klientens API.

## <a name="commands-supported-by-netx-duo-smtp-client"></a>Kommandon som stöds av NetX Duo SMTP-klienten

NetX Duo SMTP-klienten använder följande kommandon under en e-postsession med en SMTP-server.

- **EHLO** Klienten vill initiera en session som innehåller några eller alla SMTP-tjänster för tillägg som är tillgängliga från SMTP-servern. Det här är standardinställningen.
- **HELO** Klienten vill initiera en session som är begränsad till grundläggande SMTP-tjänster.
- **E-post** Klienten vill att servern ska ta emot klientens e-post.
- **Autentisering** Klienten vill initiera autentisering av servern.
- **Inlevns** Klienten vill skicka en post låda till en annan värd som det skulle innebära att e-postmeddelandet skickas till.
- **Data** Klienten vill initiera sändningen av e-postmeddelande data till servern.
- **Avsluta** Klienten vill avsluta sessionen.

## <a name="getting-started"></a>Komma igång

SMTP-klientprogrammet skapar en IP-instans och en aktiverar TCP på den IP-instansen. Sedan skapas SMTP-klienten med följande tjänst:

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

*Client_packet_pool_ptr* är en pekare till en tidigare skapad adresspool som SMTP-klienten ska använda för att skicka meddelanden till SMTP-servern.

Observera att ett program måste ange en *from_address* för den lokala enheten och en server-IP-adress. Alla adresser måste vara fullständigt kvalificerade domän namn. Ett fullständigt kvalificerat domän namn innehåller en lokal del och ett domän namn, avgränsat med ett @-tecknen. Observera att SMTP-klienten inte kontrollerar syntaxen för *from_address* eller *recipient_address* i nx_smtp_mail_sends tjänsten nedan.

När SMTP-klienten har skapats skapar SMTP-klientprogrammet ett e-postobjekt med ett korrekt formaterat SMTP-e-postmeddelande och skickar e-postmeddelandet till SMTP-klienten med följande API:

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address, UINT priority,
    CHAR *subject, CHAR *mail_body,
    UINT mail_body_length);
```

Det finns i princip ingen skillnad i att köra SMTP-klienten via IPv4 eller IPv6 från användar perspektiv. Skillnader mellan de två IP-protokollen hanteras i det underliggande NetX Duo-lagret.

Observera att ett program som vill skicka e-post måste ange en mottagar adress i *nx_smtp_client_mail* -anropet.

För autentisering kan användar namn antingen vara fullständigt kvalificerade domän namn eller Visa användar namn. Detta beror på hur servern utför autentisering.

Demon i det lilla exempel avsnittet längre fram i den här användar handboken visar hur meddelandet ska formateras. Status om e-postobjektet har skickats kommer att NX_SUCCESS. Om ett fel inträffar, om det är ett internt fel, en bruten TCP-anslutning eller att ta emot en servers Reply-felkod, returnerar *nx_smtp_mail_send* en fel status som inte är noll.

När du skickar ett e-postobjekt skapar NetX Duo SMTP-klienten en ny TCP-anslutning med SMTP-servern och påbörjar en SMTP-session. I den här sessionen skickar klienten en serie kommandon till SMTP-servern som en del av SMTP-protokollet, culminating skickar ut det faktiska e-postmeddelandet. TCP-anslutningen avbryts sedan, oavsett resultatet av SMTP-sessionen.

Efter e-postöverföringen, oavsett om det lyckas eller Miss lyckas, returneras SMTP-klienten till status "initial" och kan användas för en annan e-postöverförings session.

## <a name="netx-duo-smtp-authentication"></a>NetX Duo SMTP-autentisering

Autentisering är ett sätt för SMTP-klienter att bevisa sin identitet för SMTP-servern och få sina e-postmeddelanden levererade som betrodda användare. De flesta kommersiella SMTP-servrar kräver att klienter autentiseras.

Autentiserings data består vanligt vis av avsändarens användar namn och lösen ord. Under en verifierings utmaning frågar servern efter den här informationen och klienten svarar genom att skicka de begärda data i kodat format. Servern avkodar data och försöker hitta en matchning i dess användar databas. Om servern hittas, indikerar servern att autentiseringen har slutförts. SMTP-autentisering definieras i [RFC 2554](http://www.ietf.org/rfc/rfc2554.txt).

Det finns två varianter-autentisering, nämligen *Basic* och *Digest*. Digest stöds inte i den aktuella NetX Duo SMTP-klienten och kommer inte att diskuteras här. Grundläggande autentisering motsvarar det *namn* *och den lösenordsautentisering som* beskrivs ovan. I grundläggande SMTP-autentisering är namn och lösen ord base64-kodade. Fördelen med grundläggande autentisering är att det är enkelt att implementera och använda omfattande användning. Den största nack delen med grundläggande autentisering är namn och lösen ords data skickas på ett öppet sätt i begäran.

### <a name="plain-authentication"></a>Enkel autentisering

NetX Duo SMTP-klienten skickar ett AUTH-kommando med parametern PLAIn. Om NetX Duo SMTP-servern stöder den här typen av autentisering, kommer den att svara med en 334-svarskod. Klienten svarar med ett enda Base64-kodat användar namn och lösen ord till servern. Om servern fastställer att klientautentiseringen lyckas, svarar den med 235-lyckad kod.

### <a name="login-authentication"></a>Inloggnings autentisering

NetX Duo SMTP-klienten skickar ett AUTH-kommando med INLOGGNINGs parametern. Om NetX Duo SMTP-servern har stöd för den här typen av autentisering, kommer den att svara med en 334-svarskod som början av autentiseringen ' Challenge '. Den skickar en Base64-kodad prompt tillbaka till klienten som vanligt vis är "username". Klienten avkodar prompten och svarar med ett base64-kodat användar namn. Om servern accepterar klientens användar namn skickar den en Base64-kodad prompt för klient lösen ordet. Klienten svarar med ett base64-kodat lösen ord. Om servern fastställer att klientautentiseringen lyckas, svarar den med 235-lyckad kod.

### <a name="no-authentication"></a>Ingen autentisering

Vissa SMTP-servrar konfigureras utan autentisering. I så fall visas inte någon typ av autentisering i 250-svaret på klientens EHLO-meddelande. Inga autentiseringstyper i listan innebär dock inte nödvändigt vis att servern inte kräver eller stöder inte autentisering. Om klienten är konfigurerad för enkel autentisering eller inloggning i den här situationen, kommer NetX Duo-klienten som standard att vara vanlig. Om klienten har kon figurer ATS för ingen, hoppas autentiseringen över och SMTP-statusen går vidare till e-postläget.

Observera att om klienten har kon figurer ATS för ingen autentisering och SMTP-servern har stöd för autentisering, växlas klientens autentiseringstyp till OFORMATERAD.

## <a name="rfcs-supported-by-netx-duo-smtp-client"></a>RFC: er som stöds av NetX Duo SMTP-klienten

NetX Duo SMTP client API är kompatibelt med RFC2821 "Simple Mail Transfer Protocol" och RFC 2554 "SMTP service Extension för autentisering. “
