# Market Update

Installierbare Web-App (PWA) für Erics Market Update. Mo–Fr gegen 18 Uhr (Europe/Berlin) erscheint das tägliche Marktupdate, montags zusätzlich die 3 Top Picks der Woche.

**Keine Anlageberatung.** Informationen aus öffentlich zugänglichen Quellen, Kurse können verzögert sein.

## Aufbau
- `index.html`: App-Oberfläche, rendert `data.json` (Tabs: Heute, Top Picks, Watchlist, Archiv, Methodik)
- `data.json`: einzige Datei, die die tägliche Routine ändert
- `manifest.webmanifest`, `sw.js`, `icons/`: Homescreen-Installation und Offline-Cache

## Datenformat (`data.json`)
- `updated`: ISO-Zeitstempel der letzten Aktualisierung
- `editions[]`: neueste Ausgabe zuerst. Felder: `date`, `marketUpdate` (täglich), `weeklyPicks` (true nur bei der wöchentlichen Picks-Ausgabe), `ideas[]` (genau 3, nur bei `weeklyPicks`), `notPicked[]`, optional `noIdeasNote`. Ältere Ausgaben bis 12.11.2026 haben stattdessen `marketContext[]` und tägliche `ideas[]`.
- `marketUpdate`: `summary` (2 Zeilen), `highlights[]` (3), `drivers[{scope: global|punktuell, text, markets}]`, `regions[{name, indices[{n,v,c,note?}], note?, news[]}]` (Europa, Asien, USA), `bonds{rows[{n,v,c,note?}], comment[]}`, `commodities[{n,v,c}]`, `fx[{n,v,c}]`, `cfNews[]`, `tomorrow[]`, `sources[{t,u}]`. `c` ist ein Text wie "+0,8 %" oder "−3 bp"; das Vorzeichen steuert die Farbe.
- `ideas[]`: `ticker`, `name`, `exchange`, `country`, `sector`, `type` (Aktie: Deep Value | Wachstumsstory | GARP; sonst ETF | Hebelprodukt | Edelmetall | Rohstoff | Anleihe), `risk` (niedrig | mittel | hoch), `horizon`, `price`, `currency`, `priceDate`, `marketCap`, `fairValueLow`, `fairValueHigh`, `fairValueMethod`, `summary` (ein Satz, einfache Sprache), `explanation[]` (Absätze, einfache Sprache), `bullets[]` (Warum jetzt), `news[]`, `metrics[{l,v,x}]` (`x` = Erklärung der Kennzahl in einfacher Sprache), `qualitative[]`, `quantitative[]`, `bull`, `bear`, `catalyst{event,date}`, `glossary[{term,def}]`, `sources[{t,u}]`, `score{value,quality,momentum,catalyst (je 0–25), total, note}`, `scenarios[{name, prob (%), price, why}]` (schlecht/Basis/gut), `expectedReturn`, `riskReward`, `impliedGrowth`, `premortem`, `kill` (Bedingung, unter der die These falsch ist).
- `trackRecord` (nur in Picks-Ausgaben): `summary`, `rows[{n, v (seit Aufnahme), c (vs. Markt in pp), note}]`. Fair-Value-Felder dürfen bei ETFs/Edelmetallen/Hebelprodukten fehlen.
- `watchlist[]`: `ticker`, `name`, `added`, `priceAdded`, `lastPrice`, `lastDate`, `currency`, `fvLow`, `fvHigh`, `status` (intakt | beobachten | gebrochen), `note`

## Installation auf dem iPhone
Die Pages-URL in Safari öffnen, dann Teilen → „Zum Home-Bildschirm“.
