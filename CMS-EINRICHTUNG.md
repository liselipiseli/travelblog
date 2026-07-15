# Decap CMS für Bricks einrichten

Damit bekommst du eine `/admin`-Oberfläche zum Beiträge-Schreiben: Login mit GitHub, Formularfelder statt YAML, Bilder per Drag & Drop. Kein Code-Editor mehr nötig.

Zwei Dateien liegen bei: `config.yml` und `index.html`. Beide gehören in einen neuen Ordner `admin/` in deinem Repo `liselipiseli/travelblog`.

---

## 1. Dateien ins Repo hochladen

1. Auf GitHub im Repo `travelblog` auf **Add file → Create new file** klicken.
2. Als Dateiname `admin/index.html` eintippen (der Ordner `admin/` wird automatisch angelegt).
3. Inhalt der beiliegenden `index.html` reinkopieren, committen.
4. Gleiches Spiel für `admin/config.yml` mit dem Inhalt der beiliegenden `config.yml`.

## 2. GitHub OAuth App anlegen

Decap CMS braucht einen Login-Weg über GitHub. Netlify stellt dafür kostenlos den Authentifizierungs-Server bereit — du brauchst nur eine GitHub OAuth App und ein (leeres) Netlify-Projekt.

1. Gehe zu [github.com/settings/developers](https://github.com/settings/developers) → **OAuth Apps** → **New OAuth App**.
2. Felder ausfüllen:
   - **Application name:** z.B. „Bricks CMS"
   - **Homepage URL:** `https://liselipiseli.github.io/travelblog/`
   - **Authorization callback URL:** `https://api.netlify.com/auth/done` (exakt so, das ist wichtig)
3. **Register application** klicken.
4. Die **Client ID** notieren.
5. Auf **Generate a new client secret** klicken und das **Client Secret** notieren (wird nur einmal angezeigt).

## 3. Netlify-Projekt anlegen (nur für den Login, nicht für's Hosting)

Deine Seite bleibt komplett auf GitHub Pages. Das Netlify-Projekt dient nur dazu, den Login-Baustein bereitzustellen.

1. Kostenloses Konto auf [netlify.com](https://netlify.com) erstellen (Login mit GitHub geht am schnellsten).
2. **Add new project → Import an existing project** → GitHub auswählen → Repo `travelblog` auswählen.
3. Bei den Build-Einstellungen: **Build command** leer lassen, **Publish directory** auf `.` (Root) stellen. Fertig deployen — es ist egal, wie die Netlify-eigene Vorschau aussieht, sie wird nicht benutzt.
4. Die generierte Projekt-URL notieren, z.B. `https://verschmitzt-blau-123.netlify.app`.

## 4. OAuth in Netlify verknüpfen

1. Im Netlify-Projekt: **Project configuration → Access & security → OAuth**.
2. Unter **Authentication Providers** → **Install provider** → **GitHub** auswählen.
3. Die **Client ID** und das **Client Secret** aus Schritt 2 eintragen, speichern.

## 5. Fertig — so wird's benutzt

Ab jetzt: `https://<dein-netlify-projekt>.netlify.app/admin/` öffnen, mit GitHub einloggen, neuen Eintrag unter **Reisen (Übersicht)** oder **Reisetage** anlegen, ausfüllen, **Publish**. Die Änderung landet automatisch als Commit im `main`-Branch — GitHub Pages baut die Seite wie gewohnt neu.

Die eigentliche Blog-Adresse bleibt unverändert: `https://liselipiseli.github.io/travelblog/`.

---

## Wichtig zu wissen

- **`trip_id` und `trip_title`** müssen bei der Reise-Übersicht und allen zugehörigen Tagen exakt gleich geschrieben sein — das prüft die Oberfläche nicht automatisch, aber es ist jetzt nur noch ein Textfeld statt eines ganzen YAML-Blocks.
- **Bilder** landen jetzt alle direkt in `assets/images/` (keine Unterordner pro Reise mehr wie im alten `TEMPLATE.md`). Dateinamen bleiben trotzdem am besten kurz und beschreibend (z.B. `rom-kolosseum.jpg`), damit der Ordner übersichtlich bleibt und nichts überschrieben wird — bei Namensgleichheit hängt Decap CMS automatisch eine Nummer an.
- **Dateinamen der Beiträge** (`_posts/2026-05-01-rom.md` usw.) werden automatisch aus Datum + Reise-ID gebildet — nichts mehr von Hand tippen.
- Die alte `TEMPLATE.md` brauchst du danach nicht mehr, kann aber als Referenz im Repo bleiben.

## Falls etwas hakt

- **Login-Fenster bleibt leer/schließt sofort:** Popup-Blocker im Browser prüfen.
- **"Not Found" beim Login:** Callback-URL in der GitHub OAuth App exakt `https://api.netlify.com/auth/done` — Tippfehler sind die häufigste Fehlerquelle.
- **Änderungen erscheinen nicht auf der Seite:** GitHub Pages braucht nach jedem Commit ~1 Minute zum Neubauen — Tab unter „Actions" im Repo zeigt den Fortschritt.
