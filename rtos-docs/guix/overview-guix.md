---
title: Förstå Azure återställnings tider-GUIX och Azure återställnings tider GUIX Studio
description: Azure återställnings tider GUIX är ett högkvalitativt kvalitets paket som har skapats för att uppfylla behoven hos inbäddade system utvecklare.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827093"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Översikt över Azure återställnings tider GUIX och Azure återställnings tider GUIX Studio

Azure GUIX Embedded GUI är Microsofts avancerade, industriella klassbaserade GUI-lösning som utformats specifikt för djupt inbäddade, real tids-och IoT-program. Microsoft tillhandahåller också ett komplett design verktyg för WYSIWYG Desktop med namnet Azure återställnings tider GUIX Studio, som gör att utvecklare kan utforma sitt användar gränssnitt på Skriv bordet och generera Azure återställnings tider-GUIX inbäddad GUI-kod som sedan kan exporteras till målet. Azure återställnings tider GUIX är helt integrerat med Azure återställnings tider ThreadX återställnings tider och är tillgänglig för många av de processorer som stöds av Azure återställnings tider ThreadX. Allt detta kombinerat med en mycket liten storlek, snabb körning och överlägsen enkel användning, gör Azure återställnings tider GUIX det idealiska valet för de mest krävande inbäddade IoT-programmen som kräver ett användar gränssnitt. 

## <a name="azure-rtos-guix-api"></a>Azure återställnings tider GUIX-API

### <a name="intuitive-and-consistent-api"></a>Intuitiv och konsekvent API

* Substantiv-namn konvention för verb

* Alla API: er har ledande *gx_* för att enkelt identifiera som Azure återställnings tider GUIX

* Händelse driven programmerings modell (API)

* Fullständigt stöd för ritning av direkt arbets yta vid behov

* Enkel att interagera med Azure återställnings tider GUIX Studio-genererad kod

* API: er för linje, rektangel, polygon osv.

* API: er för cirkel, båge, cirkel, ackord, ellips osv.

* API: er för text ritning och placering

* Kant utjämning, struktur fyllningar och heldragna fyllningar

* API: er för att skapa och modifing skärmar och widgetar

### <a name="azure-rtos-guix-studio-generated-files"></a>Genererade filer för Azure återställnings tider GUIX Studio

* Automatiskt genererade ANSI C-källfiler

* Isolerar program vara från layoutinformation

* Innehåller teckensnitt och avbildningar som krävs av UI design

* Genererade filer som kompileras med program kod

* Skärmlayout kan uppdateras utan att påverka program logiken

* Resurs-ID skapa språk och tema oberoende

* Användardefinierade funktioner för anpassad ritning och händelse bearbetning

### <a name="widget-library"></a>Bibliotek för widget

* Fördefinierad men anpassningsbar uppsättning av vanliga gränssnitts element

* Mycket liten, kompakt och effektiv

* Biblioteket innehåller knappar, mätare, lista, fönster, rullning, skjutreglage, förlopps indikator, prompt och många fler

* Helt anpassningsbar ritning och utseende

* Helt anpassningsbar åtgärd och händelse hantering

* Endast widgeten som används är kopplade till program varan

### <a name="math-and-utilities"></a>Matematik och verktyg

* Funktioner för sin, cos, bågarin, arccos, tangens, kvadratroten

* Funktioner för att ändra skärm områden

* System konfiguration och start

* Minnes samlings definition (valfritt)

* Timer-hantering

* Hantering av animering

* Underhåll av lista över skadade listor

### <a name="image-processing"></a>Bearbetning av avbildning

* Funktioner för körnings avkodning av JPEG-och PNG-bilder

* Tillämpa rastrering och färg områdes konvertering

* Bild rotation

* Bild skalning

* Bild blandning

### <a name="event-processing"></a>Händelse bearbetning

* Pausar automatiskt Azure återställnings tider GUIX-tråd vid inaktivitet

* Händelse driven programmerings modell populär i UI-design

* Isolerar inmatade driv rutiner från Azure återställnings tider GUIX-ritnings tråd

* Funktioner för att skicka och ta emot händelser

* Fördefinierade händelse typer för alla typer av widgetar för Azure återställnings tider-GUIX

* Användardefinierade anpassade händelser stöds

### <a name="canvas-processing"></a>Arbets ytans bearbetning

* Underhåll av Urklipp och Z-ordning

* Isolerar bibliotek för validering från maskin varu information

* Isolerar program från maskin varu information

* Automatisk uppdatering av ändrade områden i bakgrunden

* Flera arbets ytor med skiktning och över gång stöds

* Kan anropas direkt av program varan

### <a name="input-device-drivers"></a>Driv rutin (er) för indrivmedel

* Maskin varu specifik support, Azure återställnings tider-GUIX och-program som är isolerade från maskin varu information

* Motstånds touch, Anfang och knapps ATS som stöds

* Inmatade händelser som skickas till Azure återställnings tider GUIX Event Queue

### <a name="display-drivers"></a>Visa driv rutiner

* Maskinvaruspecifika support

* Generiska driv rutiner som tillhandahålls för alla färgdjup och format

* Anpassad för att använda tillgängliga grafik acceleratorer

### <a name="target-hardware"></a>Mål maskin vara

* Nästan all maskin vara som kan hantera grafiska utdata är kompatibel med GUIX

* Flera fysiska skärmar stöds

* Minimalt RAM-och Flash-krav

## <a name="create-elegant-user-interfaces"></a>Skapa eleganta användar gränssnitt

Azure återställnings tider GUIX och Azure återställnings tider GUIX Studio innehåller alla funktioner som behövs för att skapa unika eleganta användar gränssnitt. Standard paketet för Azure återställnings tider-GUIX innehåller olika exempel användar gränssnitt, inklusive en medicinsk enhets referens, en Smart Watch-referens, en referens för start automatisering, en industriella kontroll referens, en referens för en bil och olika exempel på Sprite och animeringar. Klicka på referens exemplen som visas nedan.

### <a name="home-automation"></a>Start automatisering

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>Sjukdom

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>Konsument

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>Vita varor

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>Fordon

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>Åtnjut

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

Varje Azure återställnings tider GUIX-referens har ett motsvarande Azure återställnings tider GUIX Studio-projekt som definierar alla grafiska element i referens designen. Det är enkelt att ändra en referens design. Öppna bara motsvarande Azure återställnings tider GUIX-projekt, gör önskade ändringar, spara projektet och välj sedan *projekt*.

Generera alla utdatafiler för att generera C-koden för Azure återställnings tider-GUIX. Du behöver bara återskapa mål programmet och köra för att se den ändrade referens designen.

### <a name="small-footprint"></a>Små

Azure återställnings tider GUIX har ett remarkably litet minimalt utrymme på 13.2 KB av FLASH och 4KB RAM för grundläggande support, inklusive det minne som krävs för en arbets yta.

För en skärm med intern GRAM och själv uppdaterings teknik krävs inget minne på arbets ytan. Men för att förbättra ritnings prestanda, eller för en visnings konfiguration som inte använder den lokala delen i GRAM, definieras ett minnes område för arbets ytan av programmet.

Minnes kraven för arbets ytan är en funktion i arbets ytans storlek samt färgdjup och definieras av formeln:

<i>RAM för arbets yta (byte) = (x * y * (BPP/8))</i>

Där "x" och "y" är dimensionerna för arbets ytan (visas).

De flesta program använder sig av grafiska resurser som inte ingår i kärn lagrings kraven för Azure återställnings tider GUIX-bibliotek. Dessa resurser innehåller teckensnitt, grafiska ikoner (pixelmaps) och statiska strängar. Dessa data kan lagras i avsnittet CONST Memory (t. ex. FLASH).

Storleken på det här minnes området är beroende av ett antal faktorer, inklusive antalet och storleken på unika teckensnitt, antalet och storleken på de grafiska ikoner som används, utdataformatet och huruvida varje resurs använder komprimerade data, eftersom Azure återställnings tider GUIX stöder RLE-komprimering av både teckensnitts-och Pixelmap-data. Lagrings kraven för varje resurs visas i programmet Azure återställnings tider GUIX Studio, så att användaren kan spåra och övervaka mängden Flash-minne som kommer att konsumeras av program resurserna.

Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider-GUIX automatiskt utifrån de tjänster som faktiskt används av programmet. Detta eliminerar behovet av komplicerade konfigurations-och bygg parametrar, vilket gör det enklare för utvecklaren.

### <a name="fast-execution"></a>Snabb körning

Azure återställnings tider GUIX skrivs exklusivt i C och har utformats för snabbhet. Azure återställnings tider-GUIX har minimalt internt funktions anrops lager.

Dessutom tillhandahåller Azure återställnings tider-GUIX optimerat bortfall, ritning och händelse hantering. Allt detta och en allmän prestanda orienterad design filosofi hjälper Azure återställnings tider GUIX att uppnå snabbast möjliga prestanda.

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a>Förcertifierat av TUV till många säkerhets standarder

Azure återställnings tider GUIX har certifierats av SGS-TUV Saar för användning i säkerhets kritiska system, enligt IEC-61508 SIL 4, IEC-62304 SW säkerhets klass C, ISO 26262 ASIL D och EN 50128. Certifieringen bekräftar att Azure återställnings tider GUIX kan användas i utvecklingen av säkerhetsrelaterad program vara för de högsta säkerhets integritets nivåerna IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "fungerande säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system". SGS – TUV Saar, som bildas genom ett gemensamt företag i Tyskland SGS-Group och TUV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC-62304, ISO 26262 och EN 50128, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner, bil-och järnvägs styrnings system.

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a>Enkel, lätt att använda

Azure återställnings tider GUIX är mycket enkelt att använda och Azure återställnings tider GUIX Studio gör det ännu enklare genom att låta utvecklare visuellt utforma på Skriv bordet och generera C-kod som körs på det faktiska målet. Programmen kan sedan lägga till egna funktioner för anpassad händelse hantering och-ritning för att slutföra sitt grafiska användar gränssnitt.

Det är enkelt att använda Azure återställnings tider GUIX-API: et. Azure återställnings tider GUIX-API: et är både intuitivt och mycket funktionellt. API-namnen består av riktiga ord och inte "alfabetet soppor" och/eller de förkortade namn som är vanliga i andra fil system produkter. Alla Azure återställnings tider GUIX-API: er har en ledande *gx_* och följer en namn konvention för substantiv-verb. Det finns dessutom en funktions konsekvens i hela API: et. Till exempel kallas alla API: er som initierar ett kontroll block för widgeten &lt; widget_type &gt; _create och Create Function-parametrarna för varje widget definieras alltid i samma ordning.

### <a name="comprehensive-set-of-built-in-widgets"></a>Omfattande uppsättning inbyggda widgetar

* Azure återställnings tider GUIX innehåller en omfattande uppsättning inbyggda widgetar, inklusive:

* Drag meny

* Button (Knapp)

* Checkbox

* Cirkulär mätare

* Nedrullningsbar listruta

* Vågrät lista

* Vågrät rullnings fönstret

* Ikon

* Ikon knapp

* Linje diagram

* Meny

* Text knapp med flera rader

* Text indata från flera rader

* Text visning med flera rader

* Numerisk Pixelmap-prompt

* Numerisk prompt

* Numeriskt rullnings hjul

* Pixelmap-knapp

* Pixelmap-prompt

* Pixelmap-skjutreglage

* Pixelmap Sprite

* Förlopps indikator

* Prompt

* Förlopps indikator för radiell

* Alternativ knapp

* Rulla hjul

* Text ingång för enskild rad

* Slider

* Sträng rullnings hjul

* Text knapp

* Trädvy

* Lodrät lista

* Lodrät rullnings List

Det är enkelt för programmet att skapa egna kund-widgetar.

### <a name="complete-low-level-drawing-api"></a>Slutför rit-API på låg nivå

Azure återställnings tider GUIX innehåller ett robust Drawing-API för arbets ytor, vilket gör att programmet kan återge komplexa grafiska former.

Alla funktioner har stöd för kant utjämning på hög färg djups mål och alla former kan fyllas i vår disposition, inklusive solida och Pixelmap mönster fyllningar. Alla ritnings primitiver stöder pensel alfa vid körning med 16 BPP och högre färgdjup. Ritnings funktioner omfattar:

* Rita båge

* Cirkels rit objekt

* Linje rit

* Cirkel diagram

* Pixelmap-mix

* Pixelmap-panel

* Rita polygon

* Rita text

* Ackord Draw

* Ellips, rita

* Pixel rit

* Pixelmap Draw

* Pixelmap rotera

* Rektangel-rit

* Text blandning

### <a name="default-free-fonts-and-easy-to-add-more"></a>Standard teckensnitt som är standard och lätt att lägga till

Azure återställnings tider-GUIX innehåller en kostnads fri uppsättning TrueType-teckensnitt. Utvecklare kan lägga till ytterligare TrueType-teckensnitt som du vill.

Teckensnitts formatet för Azure återställnings tider-GUIX stöder 8bpp anti-aliasing, 4bpp kant utjämning och 1bpp monokroma teckensnitt. För de flesta resurs begränsade program återger Azure återställnings tider GUIX TrueType-teckensnitten till ett komprimerat bitmappsformat med hjälp av vårt GUIX Studio Desktop-verktyg.

### <a name="custom-jpg-and-png-decoder-implementation"></a>Implementering av anpassad JPG-och PNG-avkodare

Anpassad JPG-och PNG-avkodare implementering av JPG-och PNG-filavkodare. Den här implementeringen stöder konvertering av färg område, rastrering och körning av Azure återställnings tider GUIX-kompatibla Pixelmap format-bilder.

### <a name="extensive-display-and-touchscreen-support"></a>Omfattande skärm-och pekskärm-stöd

Azure återställnings tider GUIX innehåller allmänna visnings driv rutiner för nästan alla färg format, inklusive 1bpp monokrom, 8 BPP-palett, 8 BPP 3:3:2-format,

16 BPP 565 RGB-format, 16 BPP 4:4:4:4-format, 32 BPP x:r: g:b-format och 32 BPP a:r: g:b-format. Dessutom är Azure återställnings tider-GUIX integrerat med många av de mest populära LCD-styrenheterna och maskin varu acceleratorer (ST ChromeArt, Renesas-synergieffekter osv.).

Azure återställnings tider GUIX har fullt stöd för pekskärm (inklusive stöd för gester), pennor och virtuella tangent bords enheter.

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Verktyget Azure återställnings tider GUIX Studio Desktop WYSIWYG

Azure återställnings tider GUIX Studio innehåller en komplett design miljö för WYSIWYG-skärmen som gör det möjligt för användaren att dra och släppa grafiska element som används för att skapa GUI-skärmar. Azure återställnings tider GUIX Studio genererar automatiskt C-kod som är kompatibel med Azure återställnings tider GUIX-biblioteket, som är redo att kompileras och köras på målet. Utvecklare kan skapa förrenderade teckensnitt för användning i ett program med hjälp av det integrerade verktyget för teckensnitts generering i Azure återställnings tider-GUIX Studio. Teckensnitt kan skapas i svartvita format eller i ett kant bara alias och är optimerade för att spara utrymme på målet. Teckensnitt kan innehålla valfri uppsättning tecken, inklusive Unicode-tecken för flerspråkiga program.

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

Azure återställnings tider GUIX Studio fören klar importen av grafik från PNG-eller JPG-filer med konvertering till komprimerade Azure återställnings tider GUIX-Pixelmaps för användning i mål systemet. Många av widgetarna för Azure återställnings tider-GUIX är utformade för att införliva användar grafik för ett anpassat utseende och känsla. Dessutom tillåter Azure återställnings tider GUIX Studio anpassning av standard färger och rit format som används av Azure återställnings tider GUIX-widgetar, vilket gör att utvecklare kan justera utseendet på Azure återställnings tider GUIX mycket enkelt. Generering och underhåll av program strängar är en annan inbyggd funktion i Azure återställnings tider GUIX Studio. Detta gör det möjligt för utvecklare att utforma ett program med ett språk för utveckling och snabbt och enkelt lägga till stöd för ytterligare språk när produkten har släppts. Ett fullständigt Azure återställnings tider GUIX-program kan köras på ett dator skriv bord i Azure återställnings tider GUIX Studio-miljön, vilket gör det möjligt att snabbt och enkelt skapa och demonstrera användar koncept, testning av skärm flöden och observation av skärm över gångar och animeringar. När du är klar kan en design exporteras som mål klara C-datastrukturer som är redo att kompileras och länkas till Azure återställnings tider-GUIX och Azure återställnings tider ThreadX-bibliotek.

Azure återställnings tider GUIX och Azure återställnings tider GUIX Studio stöder flera resurs teman, vilket gör att ett program enkelt kan omväxlas i körnings läge. Teckensnitt, färger och pixelmaps kan ändras vid körning med ett enkelt API.

Läs mer om GUIX Studio

### <a name="complete-win32-simulation"></a>Slutför Win32-simulering

Azure återställnings tider-GUIX körs på en Windows-dator med exakt samma ritnings bibliotek som körs på mål tavlan. Med Azure återställnings tider GUIX kan du skapa och köra ett GUI-program på datorn och använda samma program kod på målet för fel sökning, snabb prototyper, demonstration och WYSIWYG mål operation.

### <a name="advanced-technology"></a>Avancerad teknik

* Azure återställnings tider-GUIX Advanced Technology Incorporated:

* Alpha-blandning

* Kant utjämning

* Automatisk skalning

* Bitmapps komprimering

* Kombination av arbets yta

* Stöd för anpassad widget

* Stöd för uppskjuten ritning

* Stöd för gitter

* Endian-neutral programmering

* Support för maskin varu Accelerator

* Flerspråkig support och UTF-8-kodning

* Stöd för flera skärmar och arbets ytor

* Optimerad klippning, ritning och händelse hantering

* Körnings-JPEG-och PNG-avkodare

* Skalning och teman

* Stöder monokrom till 32-bitars True-Color med alpha Graphics-format

* Stöd för över gångar, Sprite och animering

* Win32-simulering

* Fönster hantering inklusive visnings fönster och Z-ordning underhåll

### <a name="fastest-time-to-market"></a>Snabbast tid till marknad

Azure återställnings tider GUIX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla. Azure återställnings tider GUIX Studio hjälper också till att göra inbäddade GUI-design och implementering enklare. Därför är Azure återställnings tider-GUIX en av de mest populära GUI-lösningarna för inbäddade IoT-enheter. Vår konsekventa tid till marknads fördelen bygger på:

* Kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider GUIX](about-guix.md) och se själv!

* Fullständig käll kods tillgänglighet

* Lätt att använda API

* Omfattande och avancerad funktions uppsättning

## <a name="one-simple-license"></a>En enkel licens

Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.

## <a name="full-highest-quality-source-code"></a>Fullständig käll kod med högsta kvalitet

Under åren har Azure återställnings tider NetX-källkoden ställt in kvalitet och enkel förståelse. Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.

## <a name="supports-most-popular-architectures"></a>Har stöd för de flesta populära arkitekturerna

Azure återställnings tider-GUIX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande:

Avancerade arkitekturer:

**Analoga enheter**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**Arm**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M

**Takt**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**Kiseldioxid**: ESI – RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10

**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32

**Mikrohalv**: RISC-V

**NXP**: LPC, ARM7, ARM9, powerpc, 68K, I.MX, coldfire, Kinetis cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, synergieffekt

**Silicon Labs**: EFM32

**Sammanfattning**: båge 600, 700, båge EM, båg HS

**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7

**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C

**Wave-bearbetning**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class

**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE
