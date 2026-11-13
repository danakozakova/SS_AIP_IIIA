# AIP 07 — Debordelizácia priečinka

**Predmet:** AIP (AI v praxi) · **nástroj:** AI agent s prístupom k súborom (Claude Cowork, prípadne Antigravity)

> **Prečo to riešime:** Skôr či neskôr má každý priečinok, do ktorého sa bojí pozrieť — stiahnuté súbory, fotky, staré verzie dokumentov. AI agent vie taký priečinok zmapovať, navrhnúť poriadok a presúvať súbory za teba. Trik nie je v tom nechať AI „nech to spraví", ale viesť ju tak, aby sa **nič nestratilo** a aby si mal/a nad každým krokom kontrolu.

---

## Zlaté pravidlá (toto je celá pointa hodiny)

1. **AI nikdy nenecháme mazať súbory.** Všetko nechcené sa iba **presunie** do priečinka `_NA_ZMAZANIE/`. Ty si to potom prejdeš a zmažeš až vtedy, keď si istý/á.
2. **Mažeš ty, cez kôš.** Keď vymažeš súbory z `_NA_ZMAZANIE/` ručne, idú do koša — odtiaľ sa dá čokoľvek vrátiť. Nič sa teda nestratí nenávratne.
3. **Najprv zmapovať, potom sa pýtať, až potom konať.** Agent sa nesmie pustiť do upratovania skôr, než mu schváliš plán.
4. **Kontrola počtov.** Pred aj po upratovaní sa spočítajú súbory. Súčet *(ponechané + presunuté do `_NA_ZMAZANIE/`)* sa musí rovnať pôvodnému počtu. Ak nesedí, niečo sa stratilo — a to nechceme.

---

## Fáza 0 — Priprav si testovací priečinok

Na ostrom priečinku začínať nebudeme. Vyrob si cvičný „bordel", na ktorom sa dá kontrola počtov overiť:

- Vytvor priečinok `bordel_test`.
- Nahádž doň **15–20 súborov** rôzneho druhu: pár obrázkov, PDF, textové súbory, nejaké s nezmyselnými názvami (`neviem.txt`, `Kópia – kópia.docx`), zopár **duplikátov** (ten istý súbor dvakrát pod iným menom) a 1–2 prázdne súbory.
- **Zapíš si, koľko súborov tam presne je:** ...............

Tento počet budeš na konci porovnávať s kontrolným súčtom od agenta.

---

## Postup A — krok za krokom (manuálne promptovanie)

1. Spusti **Claude Cowork** (prípadne Antigravity).
2. Vytvor projekt a **pripoj priečinok** `bordel_test`, ktorý ideme debordelizovať.
3. Prvý prompt: požiadaj agenta, aby **zmapoval štruktúru** priečinka — typy a počty súborov, duplicity, prázdne a podozrivé súbory.
4. Potom nech z toho **vytvorí plán**: čo kam presunúť, čo premenovať, čo navrhnúť na zmazanie — a nech ho **zapíše do `.md` súboru** (napr. `PREHLAD_PRED.md`).
5. **Prečítaj si plán** a napíš agentovi, čo chceš inak (iné zoskupenie, iné názvy…).
6. **Zdôrazni mu, že nesmie nič mazať** — všetko nechcené len presunie do priečinka `_NA_ZMAZANIE/`. A nech si toto pravidlo zapíše aj do plánu.
7. Keď plán sedí, **schváľ ho** a daj pokyn na realizáciu.
8. Súbory z priečinka `_NA_ZMAZANIE/` si **prejdi a zmaž sám/sama** — tým idú do koša a pre istotu ich tam máš na obnovenie.
9. Nakoniec požiadaj agenta, aby **zapísal, čo sa stalo** s každým súborom (napr. do `PREHLAD_PO.md`) a aby uviedol **kontrolný súčet** počtov.

---

## Postup B — cez skill `/uprac-priecinok`

Tie isté pravidlá sa dajú zabaliť do **skillu**, aby si ich nemusel/a vypisovať zakaždým.

1. V projekte **nahraj súbor** `uprac-priecinok.skill`.
2. Pripoj priečinok `bordel_test`.
3. Spusti skill:

```
/uprac-priecinok
```

4. Ďalej už len odpovedáš na jeho otázky (čo ponechať, ako to zoskupiť, ako riešiť duplicity…).

Skill robí v podstate to isté ako postup A, plus zopár poistiek navyše: nič nemaže natrvalo, pred aj po upratovaní si **odkontroluje počty** súborov, podozrivé súbory dá bokom do `OSTATNÉ/_na_pretriedenie/` namiesto koša, a na konci vypíše prehľad, **čo sa s ktorým súborom stalo**.

---

## Kontrola — čo si na konci všimni

- Sedí **kontrolný súčet**? *(pôvodný počet = ponechané + presunuté do `_NA_ZMAZANIE/`)*  Áno / Nie
- Rozpoznal agent **duplicity**, ktoré si tam schválne dal/a? ...............
- Čo urobil so súbormi, pri ktorých si **nebol istý ani ty** (nezmyselné názvy)? ...............
- Nájdeš v prehľade každý svoj súbor v presne jednej kategórii (ponechané / premenované / presunuté / na zmazanie)? ...............

---

## Na zamyslenie

- Prečo súbory **nemaže AI**, ale ty — a prečo cez kôš?
- Načo je dobrá **kontrola počtov** pred a po? Čo by signalizovalo, keby súčet nesedel?
- Kedy sa oplatí spraviť zo svojho postupu **skill** a kedy stačí obyčajný prompt?
- Pustil/a by si tento postup rovno na priečinok s dôležitými dátami? Čo by si urobil/a *predtým*, ako prvé?

---

## Čo odovzdať

Súbory `PREHLAD_PRED.md` a `PREHLAD_PO.md`, ktoré ti agent vytvoril, a krátku odpoveď (3–4 vety) na poslednú otázku zo sekcie *Na zamyslenie*.
