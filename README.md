# Monatsplaner

Ein Aufgabenplaner in Monatsansicht. Er besteht aus einer einzigen Datei (`index.html`) und läuft kostenlos über GitHub Pages.

## Auf GitHub veröffentlichen

1. Auf github.com ein neues Repository anlegen, z. B. `monatsplaner`.
2. `index.html` hochladen („Add file → Upload files“ → „Commit changes“).
3. Unter **Settings → Pages** bei „Source“ den Eintrag *Deploy from a branch* wählen, Branch `main`, Ordner `/ (root)`, und speichern.
4. Nach etwa einer Minute ist der Planer unter `https://<dein-name>.github.io/monatsplaner/` erreichbar.

## Bedienung

- **To-do anlegen:** mit der Maus über einen Tag fahren und auf **+** klicken (oder doppelt auf den Tag klicken).
- **Bearbeiten:** auf den Namen klicken oder auf ✎.
- **Erledigt:** ✓ (das To-do wird durchgestrichen), ↺ öffnet es wieder.
- **Warteliste:** ⏸ verschiebt das To-do auf die Warteliste. Über **+** in der Warteliste kann man auch direkt dort etwas eintragen.
- **Bearbeitet (Warteliste):** ✓ ordnet das To-do einem Tag zu (vorausgewählt ist heute) und markiert es als erledigt.
- **Drag & Drop:** To-dos lassen sich zwischen Tagen und auf die bzw. von der Warteliste ziehen.
- **Extra-Info:** erscheint als Tooltip, wenn man mit der Maus über das To-do fährt (erkennbar am ⓘ).
- **Archiv:** Ein Monat wird archiviert, sobald der Folgemonat vorbei ist (September also am 1. November). Archivierte Monate sind schreibgeschützt und über das Archiv-Menü erreichbar.

## Wo werden die Daten gespeichert?

Ohne weitere Einrichtung liegen die Daten nur im Browser (localStorage), also nur auf dem Gerät, auf dem du sie eingibst. Mit **Export** und **Import** kannst du sie als JSON-Datei sichern und übertragen.

## Synchronisierung über GitHub (alle Geräte)

Mit der Synchronisierung landen die Daten als `planer.json` in einem GitHub-Repository und jedes Gerät sieht denselben Stand.

**Warum ein zweites Repository?** GitHub Pages ist kostenlos nur für öffentliche Repositories verfügbar. Lägen die Daten dort, könnte jeder deine To-dos lesen. Deshalb gehören sie in ein eigenes, **privates** Repository.

1. **Privates Daten-Repository anlegen:** github.com → „New repository“ → Name z. B. `monatsplaner-daten`, **Private** auswählen und „Add a README file“ anhaken, damit der Branch `main` existiert.
2. **Token erstellen:** Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → „Generate new token“
   - Expiration: z. B. 1 Jahr (danach einen neuen Token erstellen)
   - Repository access: **Only select repositories** → `monatsplaner-daten`
   - Permissions → Repository permissions → **Contents: Read and write**
   - Den Token kopieren. Er wird nur ein einziges Mal angezeigt.
3. **Im Planer verbinden:** auf **☁ GitHub** klicken, `dein-name/monatsplaner-daten` und den Token eintragen und auf „Verbinden“ klicken. Das wiederholst du auf jedem Gerät.

So funktioniert die Synchronisierung:
- Jede Änderung wird etwa 1,5 Sekunden später gespeichert. Oben rechts siehst du den Status (✓ synchronisiert / ⚠ Fehler).
- Kommst du zum Tab zurück, holt der Planer Änderungen von anderen Geräten.
- Hast du auf zwei Geräten gleichzeitig etwas geändert, werden die Änderungen pro To-do zusammengeführt. Bei demselben To-do gewinnt die neuere Änderung.
- Jede Speicherung ist ein Commit im Daten-Repository. Ältere Stände findest du dort in der Historie.
- Der Token wird nur im Browser des jeweiligen Geräts gespeichert und nur an `api.github.com` gesendet. Weil er nur auf das Daten-Repository zugreifen darf, kann er auch nichts anderes verändern. Auf fremden Rechnern solltest du nicht verbinden oder danach auf „Trennen“ klicken.
