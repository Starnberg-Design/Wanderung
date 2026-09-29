# Wanderkanal – Prototyp

Browser-Spiel (HTML5/JavaScript, eine einzige Datei `index.html`, keine Installation). Nur für den privaten Gebrauch.

## Starten

- **Lokal:** `index.html` per Doppelklick im Browser öffnen (Chrome, Edge, Firefox).
- **GitHub Pages:** Neues Repository anlegen, `index.html` (und optional den Ordner `assets/`) hochladen, unter *Settings → Pages* den Branch `main` und Ordner `/ (root)` wählen. Nach kurzer Zeit ist das Spiel unter `https://<dein-name>.github.io/<repo>/` erreichbar, auch auf dem Handy.
- Der Spielstand liegt im Browser (localStorage). Anderer Browser oder Gerät bedeutet anderer Spielstand.

## Bedienung

- **Zeit:** ⏸ / 1× / 2× / 4× / 8×. Tastatur: Leertaste = Pause, Tasten 1–5 = Tempo.
- **Aufnahme-Regler:** Aus / Gering / Mittel / Intensiv, jederzeit änderbar. Mehr Aufnahmen bedeuten mehr Material, aber langsameres Vorankommen und mehr Akkuverbrauch.
- **Kamerasymbole 📷:** Bei Tieren, Sehenswürdigkeiten, Unwettern und Wanderer-Interviews kurz anklicken. Bei „Aus“ sind sie grau und nicht nutzbar.
- **Aktionen:** Anhalten/Rasten, Lager auf-/abbauen, Schlafen, Feuer, Essen, Kochen, Trinken, Wasser auffüllen/behandeln, Akku laden, Erste Hilfe, Orientieren, Inventar, Tour abbrechen.
- **Auto-Essen/Trinken** und **Stopp an Wasserstellen** lassen sich abschalten.

## Was der Prototyp schon simuliert

Charakter mit 7 Fähigkeiten (Punkteverteilung), 4 Wanderungen mit Etappen/Biomen, Höhenprofil mit Steigungen, Tag-Nacht, dynamisches Wetter (Klar bis Gewitter/Sturm, Schnee bei Kälte), Wind/Temperatur/Nässe je nach Gelände, Energie, Hunger, Durst, Wärme, Nässe, Gesundheit, Schlaf (später Schlafbeginn verlängert den Bedarf, Qualität hängt von Schlafsack/Zelt/Matte/Temperatur/Nässe ab), Zelt/Tarp aufbauen, Lagerfeuer (wärmt, trocknet, kocht), Kochen mit Gaskocher, Wasserquellen, Flusswasser mit Filter/Abkochen, Brücken und Furten, Verlaufen und Orientieren (Navigationsgerät, Akku, Netz, Fähigkeit), Blasen/Verstauchung/Krankheit, Erste Hilfe, Tierbegegnungen in 5 Seltenheitsstufen inkl. Bär/Wolf-Gefahr und Bärenspray, Wanderer-Begegnungen (Tausch, Hilfe, Wegtipp, Interview), Aufnahmegeräte (Billig-Handy, Flaggschiff, Kamera, Drohne mit Flugpausen), Powerbank/Solar, Shop mit Gewicht und Rucksack-Limit, Videoauswertung mit Vielfalts-Bonus, Bewerben von Ausrüstung, Kanal mit zeitverzögerten Einnahmen und Abonnenten, Bergrettung bei Scheitern.

## Eigene Grafiken einbauen (optional)

Alles ist aktuell aus Formen und Emojis gezeichnet. Lege PNGs mit transparentem Hintergrund in einen Ordner `assets/` neben `index.html`. Fehlt eine Datei, wird automatisch der Platzhalter genutzt, du kannst also Datei für Datei austauschen.

| Ordner/Dateiname | Motiv | Empfohlene Größe |
|---|---|---|
| `assets/animals/squirrel.png`, `hare`, `marmot`, `deer`, `fox`, `reindeer`, `ibex`, `moose`, `lynx`, `eagle`, `wolf`, `bear` | Tiere, nach rechts schauend, unten bündig | ca. 256×256 |
| `assets/sights/burgruine.png`, `wasserfall`, `aussichtsturm`, `alte_steinbrücke`, `gipfelkreuz`, `bergsee`, `samische_hütte` | Sehenswürdigkeiten | ca. 320×320 |
| `assets/sprites/drone.png` | Drohne in der Luft | ca. 128×128 |
| `assets/gear/<id>.png` (z. B. `tent1`, `pack_trek`, `camera`, `drone` …) | Shop-Symbole | 96×96 |

Die Gear-IDs stehen in der Datei `index.html` im Block `const GEAR=[ … ]` (Feld `id`). Charakter, Himmel, Berge, Bäume und Zelt sind noch in Code gezeichnet. Wenn du dafür Grafiken bauen möchtest, wäre ein Charakter-Spritesheet (Laufen, Sitzen, Selfie, Landschaftsfoto, Video, Selbstgespräch, Drohnensteuerung, Kochen) der wichtigste nächste Schritt.

## Werte zum Balancen

Alle Zahlen stehen im Code und sind Startwerte:

- Energieverbrauch, Geschwindigkeit: `walkSpeedKmh()` und `bodyTick()`
- Aufnahmen pro Stunde: `SHOT_RATE`, Drohnenabstände: `DRONE_INT`
- Tierwerte: `RARITY` (Basiswert) und `ANIMALS`
- Einnahmen: `renderResult()` (Faktor 1,2) und `CURVE` (Verlauf über die Tage)
- Preise, Gewichte, Effekte: `GEAR`, `FOODS`
