# AIP 03 — Praktické základy AI · Pracovný zošit

**Predmet:** AIP — AI v praxi &emsp; **Meno:** _________________________________ &emsp; **Dátum:** _______________

---

## Bezpečné používanie AI

> AI dnes použijeme ako nástroj na učenie. **Nevkladáme do nej heslá, adresy, rodné čísla, zdravotné údaje, súkromné správy ani osobné údaje spolužiakov či zákazníkov.** Odpoveď chatbota nie je automaticky pravdivá — dôležité fakty overujeme.

**Zamysli sa:**

- Aké údaje by si do chatbota určite nenapísal?

  ................................................................................

- Ktorú školskú alebo pracovnú úlohu by bolo nefér nechať urobiť celú chatbotom?

  ................................................................................

- Na čo by mohla byť AI užitočná bez podvádzania?

  ................................................................................

---

## Aktivita 1 — AI alebo nie?

Každý výrok ohodnoť: zakrúžkuj **AI** / **nie AI** / **závisí** a stručne vysvetli prečo.

| | Výrok | Tvoja odpoveď | Prečo? |
|---|---|---|---|
| 1 | Kalkulačka vypočíta 17 × 23. | AI / nie AI / závisí | |
| 2 | YouTube alebo TikTok odporučí ďalšie video. | AI / nie AI / závisí | |
| 3 | Mobil sa odomkne podľa tváre. | AI / nie AI / závisí | |
| 4 | Excel zoradí zoznam brigád podľa zárobku. | AI / nie AI / závisí | |
| 5 | Navigácia navrhne trasu podľa aktuálnej dopravy. | AI / nie AI / závisí | |
| 6 | Chatbot prepíše tvoju poznámku do slušnej správy zákazníkovi. | AI / nie AI / závisí | |
| 7 | Termostat zapne kúrenie, keď teplota klesne pod 20 °C. | AI / nie AI / závisí | |

> 💡 **Kľúčová veta:** Nie každá automatizácia je AI. Pri AI ide o systém, ktorý na základe dát rozpoznáva vzory, robí predpovede alebo vytvára obsah.

---

## Model, chatbot a prompt

Pozri si schému:

```
Používateľ → prompt → chatbot/aplikácia → model → odpoveď
```

**Ústna úloha:** Prečítaj si tento prompt a odpovedz na otázky nižšie.

```
„Napíš krátku správu zákazníkovi, že prídem opraviť zásuvku."
```

- Čo je v tomto prípade **prompt**?

  ................................................................................

- Čo je **odpoveď**?

  ................................................................................

- Je ChatGPT/Gemini/Claude názov modelu alebo aplikácie? Prečo môže byť rozdiel dôležitý?

  ................................................................................

- Aké ďalšie informácie by si mohol pridať, aby bola správa použiteľnejšia?

  ................................................................................

---

## Aktivita 2 — Predpovedanie pokračovania

Dokonči každú vetu (napíš čo by si napísal ty, nie čo je „správne"):

1. „Hlavným mestom Slovenska je…"

   ................................................................................

2. „Keď na stavbe začne pršať, tak…"

   ................................................................................

3. „Pred prácou pod napätím vždy najprv…"

   ................................................................................

4. „V piatok po škole idem…"

   ................................................................................

5. „Tajný recept na večný život obsahuje…"

   ................................................................................

**Zamysli sa:**

- Ktorá veta mala takmer jednoznačné pokračovanie?
- Pri ktorej vete existovalo veľa rozumných pokračovaní?
- Ktoré pokračovanie mohlo znieť prirodzene, ale nemuselo byť pravdivé?

> 💡 **Kľúčová veta:** Jazykový model dobre odhaduje *pravdepodobné* pokračovanie textu. Pravdepodobné však neznamená automaticky pravdivé.

---

## Aktivita 3 — Halucinácie a overovanie

**Najprv — ešte pred tým, ako otázku zadáme chatbotu — odpovedz:**

Pre každú z nasledujúcich otázok napíš, **kde** by si odpoveď overil a čo by bol **dôveryhodný zdroj**.

**Otázka 1:**
```
Kto bol prvým človekom na Mesiaci a v ktorom roku sa to stalo?
```

- Kde overím: ................................................................................
- Dôveryhodný zdroj: ................................................................................

**Otázka 2:**
```
Aký istič a aký prierez vodiča mám použiť na okruh pre práčku?
```

- Kde overím: ................................................................................
- Dôveryhodný zdroj: ................................................................................

**Otázka 3:**
```
Nájdi vedecký článok, ktorý dokazuje, že žuvačky zvyšujú IQ o 30 %.
```

- Kde overím: ................................................................................
- Dôveryhodný zdroj: ................................................................................

---

**Po zobrazení odpovede chatbota — diskusia:**

- Je odkaz v odpovedi automatický dôkaz, že odpoveď je správna? &emsp; **Áno / Nie**
- Prečo môže byť plynulý a sebavedomý štýl chatbota nebezpečný?

  ................................................................................

---

**Mini-postup overovania — zapamataj si:**

```
1. Rozdeľ odpoveď na jednotlivé tvrdenia.
2. Vyber najdôležitejšie tvrdenie.
3. Over ho v nezávislom dôveryhodnom zdroji.
4. Skontroluj, či zdroj potvrdzuje presne dané tvrdenie.
5. Pri dôležitom alebo bezpečnostnom rozhodnutí nepouži AI ako jediný zdroj.
```

---

## Aktivita 4 — Ako písať lepší prompt: R‑Ú‑K‑F‑O

```
R – Rola:        kým má AI byť        („Si skúsený elektrikár.")
Ú – Úloha:       čo presne má spraviť  („Vysvetli, ako zapojiť zásuvku.")
K – Kontext:     pre koho a za akých okolností („Som študent, prvýkrát.")
F – Forma:       dĺžka a formát        („V bodoch, max 5.")
O – Obmedzenia:  čo dodržať / vyhnúť sa („Jednoducho, dôraz na bezpečnosť.")
```

Užitočný návyk navyše: **nechaj AI povedať, keď si niečím nie je istá** — pridaj na koniec promptu: *„Ak si pri niečom neistý, jasne to označ."*

---

**Spoločne vylepšujeme slabý prompt:**

```
Vysvetli mi istič.
```

Napíš vylepšenú verziu cez R‑Ú‑K‑F‑O:

```
R – Rola: ......................................................................................
Ú – Úloha: .....................................................................................
K – Kontext: ...................................................................................
F – Forma: .....................................................................................
O – Obmedzenia: ................................................................................
```

Môj vylepšený prompt (celý text):

................................................................................
................................................................................
................................................................................

---

**Precvičenie — vylepši sám:**

Vyber si jeden zo slabých promptov nižšie a napíš k nemu lepšiu verziu cez R‑Ú‑K‑F‑O:

```
Napíš mi niečo o elektrine.
Sprav ponuku na brigádu.
Pomôž mi s matikou.
Urob plán brigády.
Napíš správu zákazníkovi.
Oprav mi inzerát.
```

Vybraný slabý prompt: ................................................................................

Môj vylepšený prompt:

................................................................................
................................................................................
................................................................................

**Po porovnaní výstupov:**
- Čo konkrétne zlepšilo druhý prompt?

  ................................................................................

- Ktoré požiadavky chatbot splnil a ktoré nie?

  ................................................................................

---

## Záverečný kvíz

**Palec hore = pravda &emsp; Palec dole = omyl &emsp; Ruka bokom = závisí**

Označ svoju odpoveď a stručne zdôvodni:

| # | Výrok | Odpoveď | Prečo? |
|---|---|---|---|
| 1 | „AI vždy vyhľadáva na internete." | P / O / Z | |
| 2 | „Chatbot môže vytvoriť plynulý, ale nepravdivý text." | P / O / Z | |
| 3 | „Čím viac textu vložím do promptu, tým určite lepšiu odpoveď dostanem." | P / O / Z | |
| 4 | „Ak chatbot uvedie zdroj, už ho nemusím otvárať." | P / O / Z | |
| 5 | „Dobrý prompt môže obsahovať rolu, formu a obmedzenia." | P / O / Z | |
| 6 | „Hodnotu ističa od AI môžem rovno použiť bez overenia." | P / O / Z | |
| 7 | „Do chatbota môžem vložiť heslo, ak chcem, aby mi ho pripomenul." | P / O / Z | |

---

## Záverečné úlohy (vyber si jednu)

**A)** Vysvetli jednou vetou, načo je model R‑Ú‑K‑F‑O.

................................................................................

**B)** Zlepši prompt: `Napíš mi niečo o elektrine.` — napíš celý vylepšený prompt.

................................................................................
................................................................................

**C)** Na čo by si AI pri učení a práci použil ty a na čo nie?

- Použil by som na: ................................................................................
- Nepoužil by som na: ................................................................................

---

## Zadanie na odovzdanie

Vyber si **jednu reálnu vec** a vyriešiť ju cez R‑Ú‑K‑F‑O. Napríklad:
- inzerát na brigádu,
- správa zákazníkovi,
- vysvetlenie pracovného postupu.

**Odovzdaj:** prompt (celý text, ktorý si zadal) + výsledok od AI + stručný komentár: čo fungovalo, čo by si zmenil.

Odovzdanie: ................................................................................
