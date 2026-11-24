# AIP 06 — Stav hodín, faktúr a platieb

## Scenár

Si živnostník, čo sa živí poskytovaním doučovaní, konzultácií apod. Máš troch klientov: **Pixel**, **Glitch** a **Byte**. Stretnutia s nimi máš v kalendári. Na konci mesiaca potrebuješ zistiť, čo je zaplatené, čo nie, a kde sú nezrovnalosti.

Všetky dáta v tomto cvičení sú **vymyslené**. Nikdy nepúšťaj žiadny skript na vlastný Gmail s reálnymi dátami.

---

## Fáza 0 — Príprava

Prihlás sa do svojho cvičného Gmail účtu. Pošli učiteľke e-mail, aby mala tvoju adresu.

**Vyber si troch spolužiakov** — jeden bude Pixel, druhý Glitch, tretí Byte. Zapíš si, kto je kto (budeš to potrebovať viackrát).

---

## Fáza 1 — Kalendár

### 1.1 Import

1. Stiahni súbor `kalendar.ics`.
2. V Google Kalendári: **Nastavenia → Importovať a exportovať → Importovať** → vyber súbor → importuj.
3. Skontroluj, že sa ti vytvorilo **13 udalostí** v septembri 2026.

### 1.2 Pridanie hostí

1. Otvor každú udalosť „Matematika - Klient …" a v sekcii „Hostia" pridaj e-mail spolužiaka podľa toho, ktorý klient je v názve.
2. Udalosť „Príprava materiálov" nemá hosťa — tá je tvoja.
3. Spolužiak nech niektoré pozvánky **prijme** a niektoré **odmietne** (minimálne jednu nech odmietne).

### 1.3 Skript — export kalendára do CSV

Požiadaj AI (napr. ChatGPT, Claude, Gemini), aby ti napísala **Google Apps Script**, ktorý z kalendára vytiahne udalosti za september 2026 do CSV na Google Disku.

Stĺpce: `datum`, `cas_od`, `trvanie`, `nazov`, `email_hosta`, `odpoved_hosta`

**Dôležité:** Prompt pre AI si napíš sám/sama. Čím presnejšie opíšeš, čo chceš, tým lepší výsledok dostaneš.

Skript spusti na script.google.com. Keď ťa požiada o oprávnenia, **vysvetli, čo každé povolenie umožňuje**.

### 1.4 Kontrola

- Je v CSV **13 riadkov** (jeden na udalosť)?
- Má každá udalosť s hosťom vyplnený `email_hosta` a `odpoved_hosta`?
- Čo je v stĺpci `odpoved_hosta` pri odmietnutej udalosti?

---

## Fáza 2 — Faktúry

### 2.1 Úprava faktúr

1. Dostaneš 3 PDF faktúry (`FA_26090001.pdf`, `FA_26090002.pdf`, `FA_26090003.pdf`).
2. Otvor každú vo Worde (Word umožňuje otvoriť PDF na úpravu).
3. Zmeň meno klienta a e-mail na meno a e-mail svojho spolužiaka:
   - **Klient Pixel** → spolužiak, ktorého si vybral/a ako Pixel
   - **Klient Glitch** → spolužiak, ktorého si vybral/a ako Glitch
4. Ulož ako PDF.

### 2.2 Faktúry → tabuľka

Z PDF faktúr vytiahni do tabuľky (ručne alebo s pomocou AI): číslo faktúry, klient, suma, splatnosť.

---

## Fáza 3 — Bankové notifikácie

### 3.1 Prijatie mailov

Učiteľka ti pošle na Gmail **6 e-mailov** s HTML prílohami — notifikácie z Cvičnej banky. Otvor si aspoň jednu prílohu a pozri sa, čo obsahuje.

### 3.2 Skript — extrahovanie platieb

Požiadaj AI, aby ti napísala Google Apps Script, ktorý:

- nájde v schránke maily od Cvičnej banky s predmetom obsahujúcim „notifikácia"
- z HTML prílohy vytiahne riadky s časom a textom
- zapíše **prichádzajúce platby** (nie odchádzajúce!) do CSV na Google Disku
- stĺpce: `datum`, `cas`, `text`, `z_uctu`, `suma_eur`

### 3.3 Kontrola

- Počet riadkov v CSV = počet **prichádzajúcich** platieb v schránke?
- Obsahuje CSV aj odchádzajúce platby (šum)? Ak áno, oprav skript.

---

## Fáza 4 — Párovanie (AI)

### 4.1 Pravidlá párovania

**Napíš vlastnými slovami**, podľa akých pravidiel priradíš ku každej hodine faktúru a platbu. Napríklad: podľa čoho zistíš, že platba patrí ku konkrétnej faktúre? (Pozor — v notifikáciách z banky nie je variabilný symbol, len IBAN odosielateľa a suma.)

### 4.2 Výsledná tabuľka

Zadaj AI svoje pravidlá + tri CSV (hodiny, faktúry, platby) a nechaj ho vyplniť tabuľku `stav.csv`:

| datum | cas_od | klient | odpoved | faktura | stav | zaplatena_dna |
|-------|--------|--------|---------|---------|------|---------------|

Stĺpec `stav`: zaplatená / po splatnosti / zaplatená osobne

### 4.3 Porovnanie

Porovnaj svoj výsledok s riešením učiteľky. Kde sú rozdiely? Prečo?

---

## Na zamyslenie

- Prečo je nebezpečné púšťať skript, ktorý číta Gmail, na účte s reálnymi dátami?
- Kedy stačí obyčajný skript a kedy pravidlá pre AI?
- Čo robí AI, keď si nie je istá? (Pozri stĺpec „stav" — objaví sa niekde „neistá"?)
- Čo sa stane s hodinou, ktorú klient odmietol neskoro?
