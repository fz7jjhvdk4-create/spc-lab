# SPC-laborationen

Webblaboration i **statistisk processtyrning (SPC) och kapabilitetsstudier** för
högskoleingenjörsstudenter. Studenten arbetar som kvalitetsingenjör på fiktiva
*Svenska Axel AB* och genomför fem moment: variationsteori, maskinkapabilitet
(Cm/Cmk), styrdiagram (x̄/R med Western Electric-regler), processkapabilitet
(Cp/Cpk) samt förbättringsarbete med verifiering — och avslutar med en
automatiskt sammanställd labrapport.

**▶ Kör laborationen: <https://spc-lab.vercel.app>**

**📖 Ska du använda laborationen i din kurs? Läs [lärarhandledningen](LARARHANDLEDNING.md).**

## Snabbfakta

- Ingen installation, inga konton — allt körs i webbläsaren, även offline
- Varje student får unika men reproducerbara mätdata (genereras ur namnet),
  vilket möjliggör stickprovskontroll vid rättning
- Självrättande kontrollfrågor låser upp momenten i tur och ordning
- Progressionen sparas lokalt i webbläsaren; rapporten sparas som PDF
- Hela laborationen är en enda fil: [`spc-laboration.html`](spc-laboration.html)

## Drift

Sajten deployas automatiskt till Vercel vid push till `main`. För egen drift:
ladda ner `spc-laboration.html` och lägg den på valfri webbserver eller
distribuera filen direkt — den är helt fristående.
