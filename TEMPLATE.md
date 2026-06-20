# Bricks — Kopiervorlagen für neue Beiträge

Diese Datei einfach abspeichern (Notizen-App, Mac, etc.) und bei jedem neuen Beitrag den passenden Block kopieren, ausfüllen und auf GitHub als neue `.md` Datei in `_posts/` speichern.

---

## 1. EINFACHE REISE (ohne Tage-Aufteilung)

**Dateiname:** `_posts/JJJJ-MM-TT-name.md`
**Beispiel:** `_posts/2026-05-01-rom.md`

```markdown
---
layout: trip
type: trip
trip_id: HIER_KURZNAME
title: "HIER TITEL"
date: 2026-MM-TT
region: Europa
country: HIER_LAND
cities: [Stadt1, Stadt2]
duration: "X Tage"
season: "Frühling"
cover_color: "#a8c4d4"
cover_color_dark: "#5a90aa"
cover_image: HIER_BILDNAME.jpg
cover_position: "center 60%"
photo_count: 0
---
Hier der Reisetext...
```

**Pflichtfelder:** `trip_id`, `title`, `date`, `region`
**Optional aber empfohlen:** `country`, `cities`, `duration`, `season`, `cover_image`

---

## 2. REISE MIT TAGEN — ÜBERSICHTSSEITE

**Dateiname:** `_posts/JJJJ-MM-TT-name.md`
**Beispiel:** `_posts/2026-05-01-rom.md`

```markdown
---
layout: trip
type: trip
trip_id: HIER_KURZNAME
title: "HIER TITEL"
date: 2026-MM-TT
region: Europa
country: HIER_LAND
cities: [Stadt1, Stadt2]
duration: "X Tage"
season: "Frühling"
cover_color: "#a8c4d4"
cover_color_dark: "#5a90aa"
cover_image: HIER_BILDNAME.jpg
cover_position: "center 60%"
photo_count: 0
---
Kurze, persönliche Einleitung zur ganzen Reise (2-4 Sätze reichen).
```

⚠️ **Wichtig:** `trip_id` muss bei der Übersicht UND allen Tagen exakt gleich sein!

---

## 3. REISE MIT TAGEN — EINZELNER TAG

**Dateiname:** `_posts/JJJJ-MM-TT-name-tag-X.md`
**Beispiel:** `_posts/2026-05-01-rom-tag-1.md`

```markdown
---
layout: day
type: day
trip_id: HIER_GLEICHER_KURZNAME_WIE_OBEN
trip_title: "HIER GLEICHER TITEL WIE OBEN"
title: "HIER TAGES-TITEL"
date: 2026-MM-TT
day_number: 1
location: HIER_ORT
weather: "HIER WETTER"
highlight: "HIER HIGHLIGHT DES TAGES"
lat: 0.000000
lng: 0.000000
tags: [Tag1, Tag2, Tag3]
---
Haupttext des Tages hier...

## Zwischenüberschrift (optional)

![Bildbeschreibung]({{ site.baseurl }}/assets/images/HIER_BILDNAME.jpg)
*Bildunterschrift kursiv*

Weiterer Text...

> "Ein Zitat das hervorgehoben werden soll."
```

**Pflichtfelder:** `trip_id`, `trip_title`, `title`, `date`, `day_number`
**Für die Karte:** `lat` und `lng` (Koordinaten via Google Maps rechtsklick → Koordinaten kopieren)

---

## CHECKLISTE VOR DEM VERÖFFENTLICHEN

- [ ] Bilder vorher in `assets/images/` hochgeladen?
- [ ] Dateinamen der Bilder ohne Leerzeichen/Sonderzeichen?
- [ ] `trip_id` bei allen Tagen identisch geschrieben?
- [ ] `region` ist einer von: Europa, Asien, Afrika, Amerika, Ozeanien?
- [ ] Datum im Format `JJJJ-MM-TT`?

---

## KOORDINATEN FINDEN (für lat/lng)

1. Google Maps öffnen
2. Ort suchen
3. Rechtsklick auf den Pin
4. Erste Zahl = `lat`, zweite Zahl = `lng`

---

## FARBPALETTE FÜR cover_color (falls kein Bild vorhanden)

| Stimmung | cover_color | cover_color_dark |
|---|---|---|
| Blau/Meer | `#a8c4d4` | `#5a90aa` |
| Grün/Natur | `#4a7c6e` | `#1a3d33` |
| Orange/Wüste | `#c4936a` | `#7a4d28` |
| Lila/Abend | `#7a6baf` | `#221c4d` |
| Rot/Warm | `#b06e6e` | `#6b2020` |
