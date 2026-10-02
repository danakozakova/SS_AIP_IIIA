# Téma 04 — Tokeny a limity AI · pracovný list pre žiakov

**Predmet:** AIP (AI v praxi) · **úroveň:** stredne pokročilá
**Zdroj:** prepracované podľa ai.chiptron.cz/tokeny.html + vlastné aktivity

> **Prečo to riešime:** Keď rozumieš tokenom, vieš, prečo AI niekedy „zabúda", prečo dlhá konverzácia míňa viac, a hlavne — kedy stačí lacnejší/rýchlejší model. To je rozdiel medzi tým, či ti predplatné vydrží celý týždeň, alebo minieš limit v stredu.

---

## Modul 1 — Čo je token

**Token** je najmenší dielik textu, s ktorým jazykový model pracuje. **Nie je to vždy celé slovo.** Môže to byť celé časté slovo, časť slova, medzera, interpunkcia, číslo, emoji alebo časť URL.

- Krátke, časté slovo = zvyčajne 1 token.
- Dlhšie alebo zriedkavé slovo sa rozpadne na viac tokenov.
- **Slovenčina a diakritika** spotrebujú **viac** tokenov než rovnako dlhý anglický text.
- Rôzne modely delia rovnaký text **inak** (majú iné tokenizéry).

> ⚠️ Nehovor „token = štyri znaky". Je to len hrubá anglická pomôcka; pre slovenčinu, kód, čísla, emoji a URL neplatí.

### Aktivita 1 — tokenizér naživo

Otvor **OpenAI Tokenizer**: https://platform.openai.com/tokenizer
Pred každým textom **tipni**, koľko bude tokenov, potom porovnaj so skutočnosťou.

```text
Ahoj.
Dnes je pekný deň.
Nízkoenergetický.
https://www.priklad.sk/velmi-dlha-adresa?parameter=12345
😀😀😀!!!
```

**Zapíš, čo si zistil(a):**
- Zhoduje sa počet slov s počtom tokenov? ...............................................
- Ktorý riadok mal najviac tokenov a prečo? ...............................................

---

## Modul 2 — Kontextové okno (pracovný stôl)

**Kontextové okno** je maximálne množstvo tokenov, ktoré model dokáže **naraz** zohľadniť pri tvorbe odpovede. Zmestí sa doň aktuálna otázka, predchádzajúce správy, pokyny aplikácie, vložené texty aj priestor pre odpoveď.

> 🧰 **Metafora — pracovný stôl:** Model nemá pred sebou celú knižnicu ani ľudskú pamäť. Má len to, čo sa mu **práve zmestí na stôl.** Keď je stôl plný, staré veci musia dole.

### Aktivita 2 — virtuálny pracovný stôl

Predstav si, že stôl udrží **iba posledné 4 riadky.** Postupne pridávame 8 viet — pri každej novej najstaršia „padá zo stola".

```text
1. Používateľ sa volá Jožo.
2. Chce odpovede po slovensky.
3. Je v 1. ročníku strednej školy.
4. Pripravuje sa na test.
5. Má rád stručné odpovede v bodoch.
6. Pýta sa, ako si rozvrhnúť opakovanie pred testom.
7. Chce postup po krokoch.
8. Odpoveď má mať najviac päť viet.
```

Po pridaní všetkých 8 viet odpovedz **iba z toho, čo ostalo na stole:**
- Ako sa používateľ volá? .............
- V akom jazyku chce odpoveď? .............
- Na čo sa pripravuje / čo sa pýta? .............
- Aký formát chce odpoveď? .............

> Čo z toho už spoľahlivo **nevieš** určiť? Prečo?

---

## Modul 3 — Ako sa tokeny míňajú

Míňa sa **vstup** (tvoj prompt + prílohy + história) **aj výstup** (odpoveď modelu).

**Dôležité:** pri každej novej správe si model **znova načíta celú históriu** konverzácie vrátane príloh. Preto ani krátke „ďakujem" na konci dvojhodinového chatu s PDF nie je zadarmo.

Spotrebu ovplyvňujú štyri veci:
1. dĺžka tvojej otázky,
2. veľkosť kontextu (súbory, história, obrázky),
3. **použitý model,**
4. nastavenie **effort** (miera úsilia).

> ✅ **Návyk:** na novú tému začni **nové vlákno.** Ušetríš tokeny a model sa lepšie sústredí.

---

## Modul 4 — Výber modelu: netreba kanón na vrabce

Modely majú zvyčajne tri kategórie:

$$\text{ľahký} \;\longrightarrow\; \text{vyvážený} \;\longrightarrow\; \text{silný}$$

| Kategória | Na čo sa hodí | Spotreba |
|---|---|---|
| **Ľahký** (napr. Haiku) | preklady, prepisy, klasifikácia, jednoduché otázky | najnižšia |
| **Vyvážený** (napr. Sonnet) | bežné písanie, rozbory, väčšina práce | stredná |
| **Silný** (napr. Opus) | zložité analýzy, náročné ladenie, hlboké uvažovanie | najvyššia |

> 🧰 **Pravidlo:** „Na dotiahnutie jednej skrutky neberieš uhlovú brúsku." Väčšina bežnej práce nepotrebuje najsilnejší model.

- Preklad alebo zhrnutie textu → **ľahký.**
- Bežné písanie a rozbory → **vyvážený.**
- Návrh riešenia zložitého problému → **silný.**

---

## Modul 5 — Miera úsilia (effort)

Nastavenie **effort** určuje, koľko „premýšľania" model do odpovede vloží (napr. *low, medium, high, max*).

- **Nižší effort** → model odpovie priamo na otázku, rýchlo a lacno.
- **Vyšší effort** → model skúma okolie, zvažuje hraničné prípady — kvalitnejšie pri zložitom, ale drahšie.

> ✅ Na bežnú prácu stačí **medium.** *Max* len výnimočne. Keď sú odpovede slabé, skôr zvýš effort, než by si vymýšľal(a) zložité obchádzky.

---

## Modul 6 — Šikovné návyky a limity

- Limit sa meria **v tokenoch, nie v počte správ.**
- Neobnovuje sa o polnoci, ale v **posuvnom (klzavom) okne** naviazanom na tvoju prvú správu — čo minieš o 9:00, uvoľní sa neskôr (napr. o 14:00). Beží aj **týždenný strop.**
- **Kombinácia modelov:** slabší na prípravu/rozbor, silný na finále — oplatí sa, keď sa úloha dá rozdeliť. Pri úlohe, ktorá je zložitá „vcelku", radšej silný model od začiatku.

### Kuchárka návykov
- Nové vlákno na novú tému.
- Nenahrávaj zbytočne veľké súbory.
- Prepínaj model aj effort podľa náročnosti úlohy.
- Náročné dávky spusti na **začiatku** časového okna.
- Sleduj ukazovateľ spotreby (hlavne týždenný strop).

---

## Zhrnutie — čo si si mal(a) odniesť

1. Token je jednotka práce AI; token ≠ slovo.
2. Model naraz vidí len to, čo je „na stole" (kontextové okno).
3. Dlhá história = viac tokenov pri každej správe.
4. Vyber model a effort podľa náročnosti — netreba kanón na vrabce.
5. Limit sa obnovuje v posuvnom okne, plánuj náročné veci na začiatok.

**Na záver ťa čaká krátky kvíz (MS Forms).**
