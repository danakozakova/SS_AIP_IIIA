# AIP 06 — Stav hodín, faktúr a platieb

## Scenár

Si súkromná učiteľka matematiky. Doučuješ troch klientov: **Pixel**, **Glitch** a **Byte**. Cena jednej hodiny je **25 €**. Na konci mesiaca potrebuješ zistiť, čo je zaplatené, čo nie, a kde sú nezrovnalosti.

Všetky dáta v tomto cvičení sú **vymyslené**. Nikdy nepúšťaj žiadny skript na vlastný Gmail s reálnymi dátami.

---

## Fáza 1 — Príprava (Gmail, kalendár, faktúry)

### 1.1 Cvičný Gmail

Prihlás sa do svojho cvičného Gmail účtu. Pošli učiteľke e-mail, aby mala tvoju adresu.

### 1.2 Kalendár

1. Stiahni súbor `kalendar.ics` (dostaneš od učiteľky).
2. V Google Kalendári: **Nastavenia → Importovať a exportovať → Importovať** → vyber súbor → importuj.
3. Skontroluj, že sa ti vytvorilo **13 udalostí** v septembri 2026.
4. **Vyber si troch spolužiakov** — jeden bude Pixel, druhý Glitch, tretí Byte.
5. **Ku každej udalosti pridaj hosťa** — otvor udalosť, v sekcii „Hostia" pridaj e-mail spolužiaka podľa toho, ktorý klient je v názve. Udalosť „Príprava materiálov" nemá hosťa.
6. Spolužiak nech niektoré pozvánky **prijme** a niektoré **odmietne** (minimálne jednu nech odmietne).

### 1.3 Faktúry

1. Dostaneš 3 PDF faktúry (`FA_26090001.pdf`, `FA_26090002.pdf`, `FA_26090003.pdf`).
2. Otvor každú vo Worde (Word umožňuje otvoriť PDF na úpravu).
3. Zmeň meno klienta a e-mail na meno a e-mail svojho spolužiaka:
   - **Klient Pixel** → meno a e-mail spolužiaka, ktorého si vybral/a ako Pixel
   - **Klient Glitch** → meno a e-mail spolužiaka, ktorého si vybral/a ako Glitch
4. Ulož ako PDF. Faktúry si nechaj — budeš ich potrebovať neskôr.

### 1.4 Notifikácie z banky

Učiteľka ti pošle na Gmail **6 e-mailov** s HTML prílohami — notifikácie z Cvičnej banky o prichádzajúcich platbách. Otvor si aspoň jednu prílohu a pozri sa, čo obsahuje.

**Po fáze 1 máš v cvičnom Gmaile:**
- udalosti v kalendári s hosťami (spolužiakmi)
- 3 faktúry (PDF) s menami spolužiakov
- 6 notifikácií z banky (HTML prílohy v mailoch)

---

## Fáza 2 — Extrahovanie dát pomocou AI

### 2.1 Platby z notifikácií

Otvor si jednu HTML prílohu a preskúmaj jej štruktúru. Potom požiadaj AI (napr. ChatGPT, Claude, Gemini), aby ti pomohla napísať **Google Apps Script**, ktorý:

- nájde v schránke maily od Cvičnej banky s predmetom obsahujúcim „notifikácia"
- z HTML prílohy vytiahne riadky s časom a textom
- zapíše **prichádzajúce platby** (nie odchádzajúce!) do CSV na Google Disku
- stĺpce: `datum`, `cas`, `text`, `z_uctu`, `suma_eur`

**Dôležité:** Prompt pre AI si napíš sám/sama. Čím presnejšie opíšeš, čo chceš, tým lepší výsledok dostaneš.

Keď skript spustíš, povoľ oprávnenia a **vysvetli, čo každé povolenie umožňuje**.

### 2.2 Udalosti z kalendára

Napíš (s pomocou AI) druhý skript, ktorý z Google Kalendára vytiahne udalosti do CSV:

- stĺpce: `datum`, `cas_od`, `trvanie`, `nazov`, `email_hosta`, `odpoved_hosta`

### 2.3 Kontrola

- Počet riadkov v CSV platieb = počet **prichádzajúcich** platieb v schránke?
- Obsahuje CSV platieb aj odchádzajúce platby (šum)? Ak áno, oprav skript.

---

## Fáza 3 — Párovanie hodín, faktúr a platieb

### 3.1 Faktúry → tabuľka

Z PDF faktúr vytiahni: číslo faktúry, klient, suma, splatnosť. Môžeš ručne alebo s pomocou AI.

### 3.2 Pravidlá párovania

**Napíš vlastnými slovami**, podľa akých pravidiel priradíš ku každej hodine faktúru a platbu. Napríklad: podľa čoho zistíš, že platba patrí ku konkrétnej faktúre? (Pozor — v notifikáciách z banky nie je variabilný symbol, len IBAN odosielateľa a suma.)

### 3.3 Výsledná tabuľka

Zadaj AI svoje pravidlá + tri CSV (hodiny, faktúry, platby) a nechaj ho vyplniť tabuľku `stav.csv`:

| datum | cas_od | klient | odpoved | faktura | stav | zaplatena_dna |
|-------|--------|--------|---------|---------|------|---------------|

Stĺpec `stav`: zaplatená / po splatnosti / zaplatená osobne

### 3.4 Porovnanie

Porovnaj svoj výsledok s riešením učiteľky. Kde sú rozdiely? Prečo?

---

## Na zamyslenie

- Prečo je nebezpečné púšťať skript, ktorý číta Gmail, na účte s reálnymi dátami?
- Kedy stačí obyčajný skript a kedy pravidlá pre AI?
- Čo robí AI, keď si nie je istá? (Pozri stĺpec „stav" — objaví sa niekde „neistá"?)
- Čo sa stane s hodinou, ktorú klient odmietol neskoro?
