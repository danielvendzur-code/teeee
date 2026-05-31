# DERAT.sk – chatbot + kalkulačka

Samostatný widget (jeden súbor `index.html`) pre web **derat.sk** – plávajúca bublina
vpravo dole otvorí asistenta, ktorý poradí so škodcami a obsahuje **kalkulačku
orientačnej ceny** zásahu.

Postavené vo firemných farbách derat.sk: zelená `#406618`, červená `#c63a27`, font **Poppins**.

## Čo to vie
- 💬 **Chatbot** – odpovedá na časté otázky (hlodavce, hmyz, plesne, postup, bezpečnosť, cena, región).
- 🧮 **Kalkulačka v 7 krokoch** – jednoduchá, vizuálna, pre každý prípad:
  1. Služba (deratizácia, dezinsekcia, dezinfekcia, likvidácia buriny, ošetrenie stromov)
  2. Druh škodcu / problému (myši, potkany, šváby, mravce, ploštice, blchy, osy, komáre, kliešte, plesne, baktérie/vírusy…)
  3. Priestor (byt, dom, prevádzka, HoReCa, sklad, exteriér)
  4. Plocha (`m²`) alebo počet stromov – posuvník + rýchle voľby
  5. Rozsah zamorenia (mierne / stredné / silné)
  6. Doplnky (opakovaný zásah, protokol, monitoring, expres, hniezda)
  7. Zhrnutie + orientačná cena + dopytový formulár
- 📷 **Reálne fotky služieb** z derat.sk (myš, šváby, roztoče) v náhľade s jemným zoomom (Ken Burns); pri burine a stromoch ostré SVG ilustrácie.
- ✨ **Animácie** – pulzujúca bublina, „typing" indikátor chatbota, plynulé prechody krokov, count-up ceny, hover efekty. Rešpektuje `prefers-reduced-motion`.
- 📝 **Vysvetlenia služieb presne podľa derat.sk** – pri každej službe info box (potkany/myši/hraboše, postrek/zadymovanie/plynovanie, polymérová dezinfekcia…) a postup zásahu.
- 📩 **Odoslanie dopytu** funguje hneď cez predvyplnený e-mail; voliteľne aj na vlastný backend.
- 📱 Plne responzívne (na mobile fullscreen).

## Vloženie do stránky
Skopírujte obsah medzi `WIDGET ZAČIATOK` a `WIDGET KONIEC` (vrátane `<style>` a `<script>`)
do šablóny webu. Blok `<div class="demo">…</div>` je len ukážkové pozadie – na ostrej
stránke ho vynechajte.

## Úprava nastavení
Na začiatku `<script>` je objekt `COMPANY`:

```js
const COMPANY={
  phone:'+421905648129',
  phoneText:'+421 905 648 129',
  email:'info@derat.sk',     // sem chodia dopyty (mailto)
  whatsapp:'421905648129',
  leadEndpoint:''            // voliteľné: URL backendu na POST dopytu (JSON)
};
```

- **Ceny** sa upravujú v objektoch `SERVICES`, `PLACES`, `SEVERITY`, `ADDONS` – sú to
  orientačné sumy v eurách bez DPH (`base` = výjazd, `rate` = €/m² resp. €/strom,
  `mult` = násobiteľ). Minimálny výjazd je v premennej `MIN`.
- **Texty chatbota** sa upravujú vo funkcii `reply()`.
- **Fotky** sa nastavujú v objekte `PHOTO` (URL na obrázok pre danú službu). Burina
  a stromy používajú SVG z objektu `SVG`. Náhľad vykresľuje funkcia `previewHtml()`.
- **Vysvetlenia** sú v poli `info` každej služby + premenná `PROCESS` (postup zásahu).

> Ceny v kalkulačke sú **orientačné**; konečná suma sa potvrdzuje po obhliadke.
