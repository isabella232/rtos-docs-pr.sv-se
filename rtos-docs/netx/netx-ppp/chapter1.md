---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Point-to-Point Protocol (PPP)
description: NetX-program ansluter vanligtvis till det faktiska fysiska nätverket via Ethernet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4027d79f80928804a757e5801c74865389ab1d0237510e63348945ebe2b30045
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801979"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-point-to-point-protocol-ppp"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Point-to-Point Protocol (PPP)

NetX-program ansluter vanligtvis till det faktiska fysiska nätverket via Ethernet. Detta ger nätverksåtkomst som är både snabb och effektiv. Det finns dock situationer där programmet inte har Ethernet-åtkomst. I sådana fall kan programmet fortfarande ansluta till nätverket via ett seriellt gränssnitt som är anslutet direkt till en annan nätverksmedlem. Det vanligaste programprotokollet som används för att hantera en sådan anslutning är Point-to-Point Protocol (PPP).

Även om seriekommunikationen är relativt enkel är PPP något komplex. PPP består faktiskt av flera protokoll, till exempel Link Control Protocol (LCP), Internet Protocol Control Protocol (IPCP), PASSWORD Authentication Protocol (PAP) och CHAP (Challenge-Handshake Authentication Protocol). LCP är huvudprotokollet för PPP. Det är här som de grundläggande komponenterna i länken förhandlas dynamiskt på ett peer-to-peer-sätt. När de grundläggande egenskaperna för länken har förhandlats, används PAP och/eller CHAP för att säkerställa att en ansluten peer är giltig. Om båda peer-adresserna är giltiga används IPCP för att förhandla de IP-adresser som används av peer-arna. När IPCP har slutförts kan PPP skicka och ta emot IP-paket.

NetX visar PPP främst som en enhetsdrivrutin. Funktionen *nx_ppp_driver* till NetX IP create-funktionen, *nx_ip_create*. Annars har NetX ingen direkt kunskap om PPP.

## <a name="ppp-serial-communication"></a>Seriell PPP-kommunikation

NetX PPP-paketet kräver att programmet tillhandahåller en drivrutin för seriell kommunikation. Drivrutinen måste ha stöd för 8-bitars tecken och kan även använda programflödeskontroll. Det är programmets ansvar att initiera drivrutinen, vilket bör göras innan du skapar PPP-instansen.

För att kunna skicka PPP-paket måste en seriedrivrutins rutin för utdatabyte tillhandahållas till PPP (anges *i nx_ppp_create-funktionen).* Den här seriedrivrutinens byteutdatarutin anropas upprepat för att överföra hela PPP-paketet. Det är seriedrivrutinens ansvar att buffra utdata. På mottagningssidan måste programmets seriedrivrutin anropa *PPP-nx_ppp_byte_receive* när en ny byte kommer. Detta görs vanligtvis inifrån kontexten för en ISR (Interrupt Service Routine). Funktionen *nx_ppp_byte_receive* placerar den inkommande byten i en cirkulär buffert och varnar PPP-mottagningstråden om dess närvaro.

## <a name="ppp-over-ethernet-communication"></a>PPP över Ethernet-kommunikation

NetX PPP kan också överföra PPP-meddelande via Ethernet. I det här fallet kräver NetX PPP-paketet att programmet tillhandahåller en Ethernet-kommunikationsdrivrutin.

För att kunna skicka PPP-paket via Ethernet måste en utdatarutin tillhandahållas till PPP (anges *i nx_ppp_packet_send_set-funktionen).* Den här utdatarutinen anropas upprepade för att överföra hela PPP-paketet. På mottagarsidan måste programmets mottagare anropa *PPP-nx_ppp_packet_receive* när ett nytt paket anländer.

## <a name="ppp-packet"></a>PPP-paket

PPP använder AHDLC-inramning (en delmängd av HDLC) för att kapsla in alla PPP-protokollkontroller och användardata. En AHDLC-ram ser ut så här:

|**Flagga**|**Addr**|**Ctrl**|**Information**|**Crc**|**Flagga**|
|--------|--------|--------|---------------|-------|--------|
|7e |Ff|03|[0–1 502 byte]|2 byte| 7e|

Varje PPP-ram har det här övergripande utseendet. De första två bytena i informationsfältet innehåller PPP-protokolltypen. Giltiga värden definieras på följande sätt:

- C021: LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: IP-datapaket

Om den 0x0021 protokolltypen finns följer IP-paketet omedelbart. Om något av de andra protokollen finns motsvarar annars följande byte det specifika protokollet.

För att säkerställa unika 0x7E början/slutet av bildrutemarkörerna och för att stödja programflödeskontroll använder AHDLC escape-sekvenser för att representera olika bytevärden. Värdet 0x7D anger att följande tecken är kodat, vilket i princip är det ursprungliga tecknet exklusivt ORed med 0x20. Till exempel representeras 0x03 för Ctrl-fältet i rubriken av den två bytesekvensen: 7D 23. Värden som är mindre än 0x20 konverteras som standard till en escape-sekvens, samt 0x7E och 0x7D som finns i fältet Information. Observera att escape-sekvenser även gäller för CRC-fältet.

## <a name="link-control-protocol-lcp"></a>Link Control Protocol (LCP)

LCP är det primära PPP-protokollet och är det första protokollet som körs. LCP ansvarar för att förhandla om olika PPP-parametrar, inklusive den högsta mottagningsenheten (MRU) och autentiseringsprotokollet (PAP, CHAP eller ingen) som ska användas. När båda sidor av LCP är överens om PPP-parametrarna börjar autentiseringsprotokollen, om några, att köras.

## <a name="password-authentication-protocol-pap"></a>PAP (Password Authentication Protocol)

PAP är ett relativt enkelt protokoll som förlitar sig på ett namn och lösenord som anges av en sida av anslutningen (som förhandlas under LCP). Den andra sidan verifierar sedan den här informationen. Om det är korrekt returneras ett godkännandemeddelande till avsändaren och PPP kan sedan fortsätta till IPCP-tillståndsdatorn. Om antingen namnet eller lösenordet är felaktigt avvisas anslutningen.

>[!NOTE]
> Båda sidor av gränssnittet kan begära PAP, men PAP används vanligtvis bara i en riktning.

## <a name="challenge-handshake-authentication-protocol-chap"></a>Challenge-Handshake Authentication Protocol (CHAP)

CHAP är ett mer komplext autentiseringsprotokoll än PAP. CHAP-autentiseraren förser sin peer med ett namn och ett värde. Peer-datorn använder sedan det angivna namnet för att hitta en delad "hemlighet" mellan de två entiteterna. En beräkning görs sedan över ID, värde och "hemlighet". Resultatet av den här beräkningen returneras i svaret. Om det är korrekt kan PPP sedan fortsätta till IPCP-tillståndsdatorn. Om resultatet är felaktigt avvisas annars anslutningen.

En annan intressant aspekt av CHAP är att den kan ske slumpmässigt när en anslutning har upprättats. Detta används för att förhindra att en anslutning kapas – när den har autentiserats. Om en utmaning misslyckas vid någon av dessa slumpmässiga tidpunkter avslutas anslutningen omedelbart.

>[!NOTE]
> Båda sidor av gränssnittet kan begära CHAP, men CHAP används vanligtvis bara i en riktning.

## <a name="internet-protocol-control-protocol-ipcp"></a>Internet Protocol Control Protocol (IPCP)

IPCP är det sista protokollet som ska köras innan PPP-kommunikationen är tillgänglig för NetX IP-dataöverföring. Huvudsyftet med det här protokollet är att en peer informerar den andra om dess IP-adress. När IP-adressen har ställts in aktiveras NetX IP-dataöverföring.

## <a name="data-transfer"></a>Dataöverföring

Som tidigare nämnts finns NetX IP-datapaket i PPP-bildrutor med protokoll-ID:t 0x0021. Alla mottagna datapaket placeras i en eller flera NX_PACKET strukturer och överförs till NetX-mottagningsbearbetningen. Vid överföring placeras NetX-paketinnehållet i en AHDLC-ram och överförs.

## <a name="ppp-rfcs"></a>PPP-RFC:er

NetX PPP är kompatibelt med RFC1332, RFC1334, RFC1661, RFC1994 och relaterade RFC.