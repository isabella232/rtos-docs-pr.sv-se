---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Point-to-Point Protocol (PPP)
description: Vanligt vis ansluter NetX-program till det faktiska fysiska nätverket via Ethernet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9f8cd9e6e0ab086fcbf76df890c03f8d73aa1a99
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826658"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-point-to-point-protocol-ppp"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Point-to-Point Protocol (PPP)

Vanligt vis ansluter NetX-program till det faktiska fysiska nätverket via Ethernet. Detta ger nätverks åtkomst som är både snabb och effektiv. Det finns dock situationer där programmet inte har Ethernet-åtkomst. I sådana fall kan programmet fortfarande ansluta till nätverket via ett seriellt gränssnitt som är anslutet direkt till en annan medlem i nätverket. Det vanligaste program varu protokollet som används för att hantera en sådan anslutning är Point-to-Point Protocol (PPP).

Även om seriell kommunikation är relativt enkelt är PPP ganska komplex. PPP består faktiskt av flera protokoll, till exempel Link Control Protocol (LCP), Internet Protocol Control Protocol (IPCP), PAP (Password Authentication Protocol) och CHAP (Challenge-Handshake Authentication Protocol). LCP är det huvudsakliga protokollet för PPP. Det är här som bas komponenterna i länken förhandlas dynamiskt i en peer-to-peer-miljö. När grundläggande egenskaper för länken har förhandlats, används PAP och/eller CHAP för att säkerställa att en ansluten peer är giltig. Om båda peer-datorerna är giltiga används sedan IPCP för att förhandla IP-adresserna som används av peer-datorerna. När IPCP är klar kan PPP skicka och ta emot IP-paket.

NetX visar PPP-filen främst som en enhets driv rutin. Funktionen *nx_ppp_driver* anges för funktionen netx IP create, *nx_ip_create*. Annars har NetX inte några direkta kunskaper om PPP.

## <a name="ppp-serial-communication"></a>PPP-seriell kommunikation

NetX PPP-paketet kräver att programmet tillhandahåller en seriell kommunikations driv rutin. Driv rutinen måste ha stöd för 8-bitars tecken och kan också använda program flödes kontroll. Det är programmets ansvar att initiera driv rutinen, vilket bör göras innan du skapar en PPP-instans.

För att kunna skicka PPP-paket måste en seriell driv rutin för utdata från en seriell driv rutin tillhandahållas PPP (anges i funktionen *nx_ppp_create* ). Den här seriella driv Rutinens utdata-rutin kommer att anropas upprepas för att överföra hela PPP-paketet. Det är den seriella driv Rutinens ansvar att buffra utdata. På den mottagande sidan måste programmets seriella driv rutin anropa funktionen för PPP- *nx_ppp_byte_receive* varje gång som en ny byte tas emot. Detta görs vanligt vis inom ramen för en avbrotts tjänst rutin (ISR). Funktionen *nx_ppp_byte_receive* placerar inkommande byte i en cirkelformad buffert och aviserar att PPP-mottagningsfönstret har sin närvaro.

## <a name="ppp-over-ethernet-communication"></a>PPP över Ethernet-kommunikation

NetX PPP kan också överföra PPP-meddelanden över Ethernet, i det här fallet kräver PPP-paketet NetX att programmet tillhandahåller en Ethernet-kommunikations driv rutin.

För att kunna skicka PPP-paket över Ethernet måste en utmatnings rutin tillhandahållas till PPP (anges i funktionen *nx_ppp_packet_send_set* ). Den här utmatnings rutinen kommer att anropas upprepas för att överföra hela PPP-paketet. På mottagar sidan måste programmets mottagare anropa funktionen PPP *nx_ppp_packet_receive* varje gång ett nytt paket tas emot.

## <a name="ppp-packet"></a>PPP-paket

PPP använder AHDLC-ramar (en delmängd av HDLC) för att kapsla in all PPP-protokollhanterare och användar data. En AHDLC ram ser ut ungefär så här:

|**Flagga**|**Addr**|**Nedtryckt**|**Information**|**CRC**|**Flagga**|
|--------|--------|--------|---------------|-------|--------|
|7E |FF|03|[0-1502 byte]|2 byte| 7E|

Varje PPP-ram har detta övergripande utseende. De första två byten i informations fältet innehåller protokoll typen PPP. Giltiga värden definieras enligt följande:

- C021: LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: IP-datapaket

Om 0x0021-protokoll typen finns, följer IP-paketet omedelbart. Annars, om något av de andra protokollen finns, motsvarar följande byte det specifika protokollet.

För att säkerställa unika 0x7E start-och slut punkts markörer och för att stödja flödes kontroll av program vara, använder AHDLC escape-sekvenser för att representera olika byte värden. Värdet 0x7D anger att följande Character är kodat, vilket är i princip det ursprungliga tecknen exklusivt ORed med 0x20. Till exempel representeras 0x03-värdet för CTRL-fältet i rubriken av den två byte-sekvensen: 7D 23. Som standard konverteras värden som är mindre än 0x20 till en escape-sekvens, samt 0x7E-och 0x7D-värden som finns i fältet information. Observera att escape-sekvenser även gäller för CRC-fältet.

## <a name="link-control-protocol-lcp"></a>LCP (Link Control Protocol)

LCP är det primära PPP-protokollet och är det första protokollet som ska köras. LCP ansvarar för förhandling av olika PPP-parametrar, inklusive den högsta mottagnings enheten (MRU) och autentiseringsprotokollet (PAP, CHAP eller none) som ska användas. När båda sidorna av LCP samtycker till PPP-parametrar, är autentiseringsprotokollen, om det finns några, och sedan börjar körs.

## <a name="password-authentication-protocol-pap"></a>PAP (Password Authentication Protocol)

PAP är ett relativt enkelt protokoll som förlitar sig på ett namn och lösen ord som tillhandahålls av en sida av anslutningen (som förhandlas under LCP). Den andra sidan verifierar sedan den här informationen. Om det är korrekt returneras ett godkännande meddelande till avsändaren och PPP kan sedan gå vidare till datorn IPCP-tillstånd. Annars avvisas anslutningen om antingen namnet eller lösen ordet är felaktigt.

>[!NOTE]
> Båda sidor av gränssnittet kan begära PAP, men PAP används vanligt vis endast i en riktning.

## <a name="challenge-handshake-authentication-protocol-chap"></a>CHAP (Challenge-Handshake Authentication Protocol)

CHAP är ett mer komplext autentiseringsprotokoll än PAP. CHAP-autentiseraren förser sin peer med ett namn och ett värde. Motparten använder sedan det angivna namnet för att hitta en delad "hemlig" mellan de två entiteterna. Beräkningen görs sedan över ID, värde och "hemlighet". Resultatet av den här beräkningen returneras i svaret. Om detta är korrekt kan PPP fortsätta till datorn IPCP-tillstånd. Annars avvisas anslutningen om resultatet är felaktigt.

En annan intressant aspekt av CHAP är att det kan ske med slumpmässiga intervall när en anslutning har upprättats. Detta används för att förhindra att en anslutning kapas – när den har autentiserats. Om en utmaning Miss lyckas vid någon av dessa slumpmässiga tidpunkter, avbryts anslutningen omedelbart.

>[!NOTE]
> Båda sidor av gränssnittet kan begära CHAP, men CHAP används vanligt vis bara i en riktning.

## <a name="internet-protocol-control-protocol-ipcp"></a>IPCP (Internet Protocol Control Protocol)

IPCP är det sista protokoll som ska köras innan PPP-kommunikationen är tillgänglig för NetX IP-dataöverföring. Det huvudsakliga syftet med det här protokollet är att en peer ska informera den andra av dess IP-adress. När IP-adressen har kon figurer ATS aktive ras NetX IP-dataöverföring.

## <a name="data-transfer"></a>Dataöverföring

Som tidigare nämnts finns NetX IP-datapaket i PPP-ramar med protokoll-ID: t 0x0021. Alla mottagna data paket placeras i en eller flera NX_PACKET strukturer och överförs till NetX Receive-bearbetningen. Vid överföring placeras NetX-paketets innehåll i en AHDLC-ram och överförs.

## <a name="ppp-rfcs"></a>PPP-RFC

NetX PPP är kompatibelt med RFC1332, RFC1334, RFC1661, RFC1994 och relaterade RFC: er.