# Hodina AI: stav hodín, faktúr a platieb (2 týždne, vymyslené dáta)

## Čo žiaci dostanú
Každý cvičný Gmail dostane 3 maily od učiteľky: **notifikácie z Cvičnej banky** (HTML príloha), **faktúry** (PDF) a **kalendár** (.ics na import). Dáta sú vymyslené a pre každý účet trochu iné (sumy, dátumy, chyby).

## Týždeň 1: dáta zo schránky a kalendára do CSV (2 × 45 min)
1. Importuj `kalendar.ics` do Google Kalendára cvičného účtu (Nastavenia → Importovať).
2. Zadanie pre AI (žiak si ho upraví): *"Napíš Google Apps Script, ktorý z mojej Gmail schránky nájde maily od ... s predmetom ..., z HTML prílohy vytiahne riadky s časom a textom a prichádzajúce platby zapíše do CSV na Disku. Pošli upozornenie e-mailom, ak zlyhá."*
3. Druhý skript: udalosti kalendára → CSV (dátum, čas, trvanie, názov, e-mail, odpoveď).
4. Žiaci spustia skripty, povolia oprávnenia a **vysvetlia, čo každé povolenie umožňuje**.
5. Kontrola: počet riadkov v CSV zodpovedá počtu platieb v schránke.

## Týždeň 2: párovanie (2 × 45 min)
1. Z faktúr (PDF) vytiahnu číslo, klienta, sumu a splatnosť (ručne alebo cez AI).
2. Žiaci **slovne napíšu pravidlá párovania** hodina → faktúra → platba (e-mail klienta, dátum, suma, účet platiteľa).
3. AI podľa pravidiel vyplní `stav.csv` so stĺpcami: datum, cas_od, trvanie, nazov, email, odpoved, faktura, stav, zaplatena_dna.
4. Porovnanie s riešením učiteľa, rozbor chýb.
5. Diskusia: kedy stačí obyčajný skript a kedy pravidlá pre AI? Čo robí AI, keď si nie je istá (stav "neistá")?

## Čo je v dátach schválne (pasce)
- hodina odmietnutá neskoro, ktorá sa stále fakturuje,
- hodina bez účastníka (osobná, "zaplatená osobne"),
- klient, ktorý platí po každej hodine rovnakú sumu bez faktúry,
- faktúra za viac hodín naraz,
- nezaplatená faktúra po splatnosti,
- platba od neznámeho platiteľa (súkromná),
- šum v notifikácii (odchádzajúca platba).

## Bezpečnosť a etika (téma na diskusiu)
Nikdy nepúšťať skript na vlastný Gmail s reálnymi dátami. Povolenie čítať poštu je veľká moc. Čo sa môže stať, keď cudzí skript dostane prístup? Prečo sú všetky dáta v tejto hodine vymyslené?

## Pre učiteľku
1. `python3 generator.py 20` vytvorí `balik/ucet_01 ... ucet_20` a `riesenie/` (riešenie pre každý účet).
2. Balík nahraj na Disk, do rovnakého priečinka daj `ucty.csv` (vzor `ucty_vzor.csv`: číslo;e-mail).
3. V `posli_maily.gs` nastav `FOLDER_ID` a rozsah účtov `ZACIATOK`/`KONIEC` pre skupinu. Spusti `posli()`. Každý účet dostane 3 maily, limit sa zmestí aj pre 20 účtov v jeden deň.
4. Riešenie jednotlivých účtov je v `riesenie/riesenie_ucet_NN.csv`.
