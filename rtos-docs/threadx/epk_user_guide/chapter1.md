---
title: Kapitel 1 – Introduktion till körnings profil paketet
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider ThreadX Execution Profile Kit (EPK).
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30676437535229ad5bdbca10dcc9ca009d6e74
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377654"
---
# <a name="chapter-1--introduction-to-the-execution-profile-kit"></a>Kapitel 1 Introduktion till körnings profil paketet

ThreadX Execution Profile Kit (EPK) innehåller en infrastruktur för program för att dynamiskt spåra körnings tid för trådar, avbryta tjänst rutiner (ISR: er) och inaktiva system förhållanden. Detta är särskilt användbart för optimering och justering av programmet för högsta prestanda. Men det är också ett värdefullt fel söknings stöd.

EPK förlitar \" sig på hookar \" som är inbyggda i ThreadX-schemaläggnings logiken i en sammansättnings kod som anropas för tråd post, tråd avslutning, ISR-post och ISR-utgång. EPK-rutinerna beräknar tiden i mellan sådana händelser och lagrar delta tiden i globala variabler samt medlemmar i kontroll blocket för **TX_THREAD** .

> [!NOTE]
> *Utvecklaren är kostnads fri att ändra eller till och med ersätta dessa Hook-funktioner med sin egen logik för att växla i/O-PIN-kod för att tillhandahålla maskin varu synlighet till ett ThreadX program som körs*.

## 

## <a name="epk-requirements"></a>Krav för EPK

EPK kräver ThreadX 6,0 (eller senare) för att kunna fungera. EPK kräver också en \" rimlig \" lösning, vilket ökar maskin varu tids källan. Den mest rimliga lösningen skulle vanligt vis vara något på en andra skala. Om upplösningen är för fantastisk, kommer EPK-räknarna att max gränsen för snabbt. Om upplösningen är för liten går det inte att göra något korrekt. Programmets tids källa definieras i ***tx_execution_profile. h** _ av makrot _ * TX_EXECUTION_TIME_SOURCE * *.

C-kompilatorn måste ha stöd för \" signerad typ som är lång \" för osignerade 64-bitars räknare. Dessutom antar EPK att de globala variablerna initieras av kompilatorns start kod för körning. Om detta inte är fallet måste de globala variabler som definieras i ***tx_execution_profile. c*** initieras till 0 av programmet.

## <a name="epk-installation"></a>EPK-installation

Installera ThreadX-EPK genom att följa stegen nedan och återskapa hela ThreadX-biblioteket och programmet.

1. Inkludera källfilerna för EPK (***tx_execution_profile. h** _ och _*_tx_execution_profile. c_*_) i ditt ThreadX Library build-projekt. Dessa filer kan finnas i [Azure återställnings tider ThreadX-lagrings platsen](<https://github.com/azure-rtos/threadx>) under mappen _ *_Utility/Execution_Profile_**.

1. I ***tx_port. h** _ definierar du \*TX_THREAD_EXTENSION_3** makrot på följande sätt.
```
    #define TX_THREAD_EXTENSION_3 unsigned long long tx_thread_execution_time_total; \
    unsigned long tx_thread_execution_time_last_start;
```

3. Definiera **TX_EXECUTION_TIME_SOURCE** makro i **_tx_execution_profile. h_** för att mappa till din maskin varu tids källa.

1. Se till att build-miljön definierar **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** så att schemaläggnings-hookarna anropas från sammansättnings koden för ThreadX.

1. Om du vill använda 64-bitars tids källa läser du filen ***tx_execution_profile. h*** för instruktioner om hur du kan göra detta.

1. Återskapa hela biblioteket och programmet så att alla dessa alternativ är korrekt kompilerade.

Du är nu redo att använda EPK med ditt program.

##  <a name="epk-example"></a>EPK-exempel 

Följande är ett exempel på EPK som används i en vanlig ThreadX-demonstration, som kon figurer ATS med en 32-bitars timer-källa som ökar 7,2 gånger per mikrosekund. 

**TX_EXECUTION_TIME_SOURCE** makrot har definierats för att hämta den Minnesmappat timer-registreringen på 0xE0001004 enligt följande.
```
(EXECUTION_TIME_SOURCE_TYPE) \*((ULONG \*) 0xE0001004)
```

Att låta demonstrationen köras i fem sekunder ger följande resultat.

![Resultat för att köra demonstrations körningen.](media/demo_results.png)

Eftersom standard demonstrationen av ThreadX inte har någon inaktiv tid (trådar 1 och 2 körs kontinuerligt), rapporterar EPK på rätt sätt noll för inaktivitet. Den totala ISR-tiden och tråd värden kan divideras med 7,2 för att kunna härleda mikrosekunderna för varje körnings kategori. EPK tillhandahåller också API: er för att få åtkomst till den här informationen (se mer information finns i [kapitel 2](chapter2.md)).