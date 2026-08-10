# Lärarhandledning — SPC-laborationen

*Webblaboration i statistisk processtyrning och kapabilitetsstudier för högskoleingenjörer*

**Laborationen körs på: <https://spc-lab.vercel.app>**

---

## 1. Översikt

| | |
|---|---|
| **Målgrupp** | Högskoleingenjörsstudenter, t.ex. industriell ekonomi, maskinteknik |
| **Tidsåtgång** | 2–3 timmar (inklusive kontrollfrågor och reflektioner) |
| **Förkunskaper** | Grundläggande statistik: normalfördelning, medelvärde, standardavvikelse |
| **Utrustning** | Valfri enhet med webbläsare — dator eller surfplatta rekommenderas, mobil fungerar |
| **Installation** | Ingen. Öppna länken, klart. Fungerar även offline (se avsnitt 8) |
| **Examination** | Studenten sparar sin labrapport som PDF och laddar upp den på kursens lärplattform |

Laborationen är byggd kring en berättelse: studenten är nyanställd kvalitetsingenjör
på det fiktiva företaget *Svenska Axel AB*, där CNC-svarven *Svarv 3* (CNC =
*Computer Numerical Control*, datorstyrd verktygsmaskin) tillverkar axlar
med kravet **Ø 25,000 ± 0,050 mm**. Kunden klagar på kasserade axlar, och studenten
ska reda ut varför — och åtgärda det.

### Lärandemål

Efter genomförd laboration kan studenten:

1. förklara skillnaden mellan **slumpmässiga och urskiljbara orsaker** till variation,
2. genomföra och tolka en **maskinkapabilitetsstudie** (Cm, Cmk) och förklara varför
   läge och spridning är två skilda problem,
3. upprätta **styrdiagram** (x̄- och R-diagram), beräkna styrgränser ur processdata och
   ställa diagnos på instabila processer med hjälp av mönsterregler (Western Electric),
4. genomföra och tolka en **processkapabilitetsstudie** (Cp, Cpk) och förklara varför
   processkapabiliteten alltid är sämre än maskinkapabiliteten,
5. prioritera **förbättringsåtgärder** utifrån hur variationskällor adderas kvadratiskt,
   och verifiera förbättringar med data (PDCA — Planera–Gör–Studera–Lär).

---

## 2. Så fungerar appen

- **Studentens namn blir datafrö.** Alla mätvärden genereras deterministiskt ur namnet
  som skrivs in på startskärmen. Varje student får därmed **unika data** (labbkompisen
  kan inte kopiera siffror), men **samma namn ger alltid exakt samma data** — vilket du
  som lärare kan använda för stickprovskontroll (se avsnitt 6).
- **Momenten låses upp i tur och ordning.** Nästa moment öppnas först när både
  momentets uppgift är avklarad *och* kontrollfrågorna är rätt besvarade.
- **Kontrollfrågorna är låsta** (gråade) tills momentets praktiska uppgift är klar —
  studenten måste laborera innan hen svarar. Alla frågor rättas direkt i appen med
  förklarande feedback, och studenten kan försöka tills allt är rätt.
- **Progressionen sparas automatiskt** i webbläsarens lokala lagring. Studenten kan
  stänga sidan och fortsätta senare — **på samma enhet och i samma webbläsare**.
  Ingen data lämnar enheten (inga konton, ingen server, GDPR-vänligt).
- **Ordlista** finns i menyraden; facktermer i texten är dessutom klickbara
  (blå prickad understrykning) med kortförklaringar.

---

## 3. Momenten — vad studenten möter och vad som är avsiktligt inbyggt

Som lärare bör du känna till de pedagogiska "fällor" som är medvetet konstruerade.
**Berätta inte om dem i förväg** — aha-upplevelserna är laborationens kärna.

### Moment 0 · Introduktion och teori (~20 min)
Interaktiv normalfördelning där studenten drar i reglage för läge (μ) och spridning (σ)
mot toleransgränserna och ser kassationen i ppm (parts per million) ändras live. Uppgiftskravet är att båda
reglagen använts. Grundbegrepp: slumpmässiga/urskiljbara orsaker, toleransgränser
(kundens röst) kontra styrgränser (processens röst).

### Moment 1 · Maskinkapabilitet, Cm/Cmk (~30 min)
Studenten "tillverkar" 50 axlar i följd och beräknar Cm och Cmk mot kravet ≥ 1,67.
Alla formler visas ifyllda med studentens egna siffror, steg för steg.

> **Inbyggt:** Maskinen är **alltid felcentrerad** från start. Första studien ger
> godkänt Cm (typiskt 2,2–2,9) men underkänt Cmk (typiskt 1,1–1,45). Studenten måste
> inse att problemet är läget, inte spridningen, räkna ut rätt verktygsoffset ur sitt
> x̄ och köra en ny studie. Vanligaste misstaget: att glömma att justeringen görs
> *relativt nuvarande offset* (ny offset = gammal offset + (25,000 − x̄)).

### Moment 2 · Styrdiagram, x̄/R (~40 min)
Styrgränser beräknas ur 25 provgrupper (n = 5) med konstanterna A₂ = 0,577, D₃ = 0,
D₄ = 2,114. Därefter övervakar studenten fyra "produktionsveckor" (20 provgrupper
vardera) och ställer diagnos: stabil process, nivåskifte, trend eller ökad spridning.
Appen rättar mot Western Electric-reglerna och markerar larmen i facit.

> **Inbyggt:** De fyra veckorna innehåller exakt en av varje störningstyp, men i
> **slumpad ordning per student** — grannens vecka B är inte samma som din.
> Spridningsscenariot syns främst i R-diagrammet, vilket motiverar varför båda
> diagrammen behövs.

### Moment 3 · Processkapabilitet, Cp/Cpk (~30 min)
En hel produktionsvecka simuleras: 5 dagar × 2 skift × 25 axlar = 250 mätvärden, med
materialpartier (mellan skift), verktygsslitage (inom skift), temperaturdrift vid
skiftstart och kvarvarande lägesfel. Cp och Cpk beräknas mot kravet ≥ 1,33.

> **Inbyggt:** Resultatet är **alltid underkänt** — typiskt Cp ≈ 1,0–1,3 och
> Cpk ≈ 0,8–1,1 — trots att maskinen klarade 1,67 med marginal i moment 1.
> Jämförelsevyn Cm mot Cp är laborationens viktigaste bild: samma maskin, samma
> toleranser, men fler variationskällor över tid. I individvärdesdiagrammet kan
> studenten *se* källorna: nivåhopp mellan skift, drift inom skift.

### Moment 4 · Förbättra och verifiera (~30 min)
Studenten väljer förbättringsåtgärder inom en budget på **80 kkr** (kilokronor =
tusen kronor) och verifierar med en ny veckostudie. Mål: Cpk ≥ 1,33. Åtgärderna:

| Åtgärd | Kostnad | Effekt (dold för studenten) |
|---|---|---|
| Centrera processen | 0 kr | Tar bort lägesfelet |
| Varmkörningsrutin | 15 kkr | Tar bort temperaturdriften (liten källa) |
| Tätare verktygsbyten | 20 kkr | Halverar slitagets vandring |
| Materialstyrning | 40 kkr | Minskar största spridningskällan (partivariationen) till ca 40 % |
| Ny precisionsfixtur | 55 kkr | Minskar maskinens egen spridning ca 20 % |

> **Inbyggt:** Enbart centrering räcker **inte** (spridningen är för stor). Den dyra
> fixturen är nästan verkningslös — maskinen är redan bra, och källor adderas
> kvadratiskt (σ²tot = σ₁² + σ₂² + …). Nyckeln är att centrera (gratis) och angripa
> **materialvariationen**, den största källan. Fungerande kombinationer inom budget är
> t.ex. centrera + materialstyrning (40 kkr) eller centrera + verktygsbyten +
> materialstyrning (60 kkr). Misslyckade försök kostar "en produktionsvecka" och ger
> en ledtråd om största kvarvarande källa — studenten får försöka igen. Efter godkänd
> verifiering visas en processanalys med alla variationskällor före/efter, inklusive
> hur lite de icke åtgärdade källorna flyttade sig.

### Labrapporten
Sammanställer automatiskt allt: metadata, alla studier med nyckeltal, diagram,
styrdiagramsbedömningar med facit, förbättringsförsök, quizresultat och studentens
reflektionssvar. Sparas som PDF via webbläsarens utskriftsdialog.

---

## 4. Genomförande — förslag på upplägg

**Före passet**
1. Testa själv! Gör laborationen en gång med ditt eget namn (2–3 h första gången).
2. Dela länken <https://spc-lab.vercel.app> via lärplattformen.
3. Be studenterna ta med dator eller surfplatta (mobil går men är trängre).
4. Påminn: **använd samma enhet och webbläsare hela laborationen** (progressionen
   sparas lokalt), och **stäng inte privat-/inkognitoläge** (då sparas inget).

**Under passet**
- Låt studenterna arbeta självständigt — appen är självinstruerande. Din roll blir
  främst att fördjupa: fråga "varför blev Cmk lägre än Cm?", "var i veckodiagrammet
  ser du verktygsbytet?".
- Momenten 0–2 hinns oftast på första halvan; 3–4 plus rapport på andra.
- Uppsamling i helklass efter moment 3 rekommenderas: låt några studenter jämföra
  sina Cm/Cp-värden — alla har olika siffror men samma mönster. Det är en utmärkt
  diskussionsstart.

**Efter passet**
- Studenten sparar rapporten som PDF (knappen "Skriv ut / spara som PDF", helst från
  dator) och laddar upp på lärplattformen.

---

## 5. Bedömning

Rapporten innehåller allt underlag. Förslag på godkänt-kriterier:

- [ ] Samtliga moment genomförda (rapporten avslutas då med stämpeln *"Laboration genomförd"*)
- [ ] Moment 1: minst två studier — en underkänd följd av en godkänd efter centrering
- [ ] Moment 2: minst 3 av 4 veckor rätt diagnostiserade (syns i rapportens facittabell)
- [ ] Moment 4: verifierat Cpk ≥ 1,33 inom budget
- [ ] Reflektionsfrågorna besvarade med egna resonemang (se nedan)

Reflektionsfrågorna (en per moment, fritext, följer med i rapporten) är det bästa
underlaget för att bedöma förståelse snarare än genomförande:

1. *Moment 0:* Skillnaden slumpmässiga/urskiljbara orsaker, med eget exempel.
2. *Moment 1:* Varför räcker inte Cm? Hur resonerade du vid justeringen?
3. *Moment 2:* Varför behövs mönsterregler utöver "punkt utanför styrgräns"?
4. *Moment 3:* Jämför ditt Cm med ditt Cp — vilka källor bidrog, och var syntes de?
5. *Moment 4:* Vilka åtgärder valde du och varför? Vad om budgeten halverats?

I rapporttabellen för moment 4 framgår också **antal försök** — många försök med
dyra, verkningslösa kombinationer kan vara ett samtalsunderlag om förståelsen av
kvadratisk addition.

---

## 6. Stickprovskontroll av inlämnade rapporter

Eftersom alla mätdata genereras deterministiskt ur studentens namn kan du verifiera
en rapport: öppna laborationen själv, skriv in **exakt samma namn** (skiftläge spelar
ingen roll) — du får då **identiska mätvärden, Cm/Cmk/Cp/Cpk och styrdiagram** som
studenten. Avvikande siffror i en inlämnad rapport betyder att något inte stämmer.

Observera att kontrollen förutsätter samma version av laborationen som studenten
använde. Vid större uppdateringar av simuleringen ändras genererade data — gör därför
stickprov i nära anslutning till kursomgången.

---

## 7. Vanliga frågor och problem

| Situation | Förklaring / åtgärd |
|---|---|
| "Kontrollfrågorna är gråa" | Avsiktligt — momentets praktiska uppgift måste göras klart först. Kravet står i den gula rutan. |
| "Jag kommer inte vidare till nästa moment" | Både uppgift och quiz måste vara gröna i rutan längst ner i momentet. |
| "Min studie blir aldrig godkänd i moment 1" | Kontrollera offsetberäkningen: ny offset = nuvarande offset + (25,000 − x̄). Vanligt fel: man sätter offset = avvikelsen i stället för att addera. |
| "Cpk blir inte godkänt i moment 4 trots åtgärder" | Fråga: är processen centrerad? Vilken är största spridningskällan? (Ledtråd ges i appen efter varje misslyckat försök.) |
| "All min progression är borta" | Annan enhet, annan webbläsare eller rensad webbdata. Progressionen ligger lokalt i webbläsaren. Med samma namn återskapas samma *data* snabbt, men momenten måste klickas igenom igen. |
| "Tabellen syns inte hela på mobilen" | Svep i sidled i tabellen. |
| Studenten vill börja om | Knappen "Nollställ hela laborationen…" finns i rapportvyn. |
| Två studenter har likadana siffror | Ska inte inträffa om de använt olika namn — kontrollera namnen i rapporthuvudet (se även avsnitt 6). |

---

## 8. Teknik, drift och anpassning

- **Arkitektur:** hela laborationen är **en enda HTML-fil** utan externa beroenden —
  ingen server, inga konton, ingen datainsamling. Slumptalen genereras med seedad
  generator (namnet hashas till frö); statistiken (φ-funktion, kapabilitetsindex,
  styrgränskonstanter, Western Electric-regler) beräknas i webbläsaren.
- **Källkod:** <https://github.com/fz7jjhvdk4-create/spc-lab> (filen
  `spc-laboration.html`). Ändringar som pushas till `main` publiceras automatiskt
  på <https://spc-lab.vercel.app>.
- **Egen drift:** ladda ner `spc-laboration.html` och lägg den på valfri kurswebb,
  eller dela filen som den är — den fungerar helt offline (dubbelklicka för att öppna).
- **Anpassning:** artikeldata och toleranser ligger samlade i konstanten `SPEC`
  (mål 25,000, tolerans ± 0,050), kravnivåerna (1,67/1,33) i respektive moments
  logik, quizfrågorna i `QUIZ` och reflektionsfrågorna i `REFLECT` — allt i samma fil.
  Observera att ändrade simuleringsparametrar ändrar alla studenters data (påverkar
  stickprovskontrollen, avsnitt 6).

---

## 9. Koppling till litteratur

Terminologi och arbetsgång följer svensk kvalitetsteknisk standard såsom den lärs ut i
t.ex. Bergman & Klefsjö, *Kvalitet från behov till användning*: duglighetsindex
Cm/Cmk (maskin, krav 1,67) och Cp/Cpk (process, krav 1,33), styrdiagram med
provgrupper och A₂/D₃/D₄-konstanter, samt förbättringscykeln PDCA. I laborationen
används genomgående den totala standardavvikelsen s; skillnaden mot
inomgruppsskattningen R̄/d₂ (Cp/Cpk kontra Pp/Ppk enligt AIAG, *Automotive Industry
Action Group* — den amerikanska fordonsindustrins standardiseringsorganisation) tas upp i en
fördjupningsruta i moment 3.

---

*Frågor eller förbättringsförslag? Öppna gärna ett ärende på
<https://github.com/fz7jjhvdk4-create/spc-lab/issues>.*
