# Daily Stock Ideas

Installierbare Web-App (PWA) für tägliche Aktien-Research-Ideen. Mo–Fr gegen 12:30 Uhr (Europe/Berlin) erscheint eine neue Ausgabe.

**Keine Anlageberatung.** Ideen aus öffentlich zugänglichen Quellen, Kurse können verzögert sein.

## Aufbau
- `index.html`: App-Oberfläche, rendert `data.json`
- `data.json`: einzige Datei, die das tägliche Update ändert
- `manifest.webmanifest`, `sw.js`, `icons/`: Homescreen-Installation und Offline-Cache

## Datenformat (`data.json`)
- `updated`: ISO-Zeitstempel der letzten Aktualisierung
- `editions[]`: neueste Ausgabe zuerst. Felder: `date`, `marketContext[]` (leer bzw. weglassen, wenn nicht relevant), `ideas[]` (0–5), `notPicked[]`, optional `noIdeasNote`
- `ideas[]`: `ticker`, `name`, `exchange`, `country`, `sector`, `type` (Deep Value | Wachstumsstory | GARP | Anleihe | Edelmetall | Rohstoff | ETF), `risk` (niedrig | mittel | hoch), `horizon`, `price`, `currency`, `priceDate`, `marketCap`, `fairValueLow`, `fairValueHigh`, `fairValueMethod`, `metrics[{l,v}]`, `bullets[]` (3–5), `bull`, `bear`, `catalyst{event,date}`, `sources[{t,u}]`
- `watchlist[]`: `ticker`, `name`, `added`, `priceAdded`, `lastPrice`, `lastDate`, `currency`, `fvLow`, `fvHigh`, `status` (intakt | beobachten | gebrochen), `note`

## Installation auf dem iPhone
Die Pages-URL in Safari öffnen, dann Teilen → „Zum Home-Bildschirm“.
