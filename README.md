# Mein Gesundheits-Tracker – Version 2.0

Eine kostenlose, lokal speichernde iPhone-Web-App für die **14 Excel-Kriterien** in Ernährung, Schlaf und Bewegung. Keine Registrierung innerhalb der App, kein Server für persönliche Einträge.

## Sicheres Update von Version 1 (unbedingt in dieser Reihenfolge)

1. **Am iPhone die bisherige App öffnen**, Reiter **Daten** → **JSON sichern**. Backup in der App **Dateien** bzw. iCloud Drive ablegen. Falls du die Originaldaten erneut brauchst, gibt es zusätzlich das private ursprüngliche JSON-Backup aus der vorherigen Unterhaltung.
2. **GitHub** → Repository `gesundheits-tracker` → **Add file → Upload files** öffnen.
3. Alle **sieben Web-Dateien** aus diesem ZIP direkt in das **Hauptverzeichnis** laden: `index.html`, `style.css`, `app.js`, `sw.js`, `manifest.webmanifest`, `icon.svg`, `data.js`. `README.md` ist optional. Bei gleichnamigen Dateien die vorhandene Fassung durch die neue ersetzen. **Keine ZIP-Datei und keine Gesundheits-Backups hochladen!**
4. Änderungen mit **Commit changes** bestätigen. GitHub Pages verwendet weiter **Settings → Pages → Deploy from a branch → main → /(root)**.
5. Die GitHub-Pages-Adresse **auf dem iPhone in Safari öffnen** und neu laden. Eine bereits installierte Home-Bildschirm-Web-App sollte dieselbe URL weiterverwenden. Bei altem Bildschirm: die Website in Safari einmal neu laden und die App vollständig schließen/neu öffnen. GitHub Pages und Service Worker können ein wenig zur Aktualisierung benötigen.
6. **Daten prüfen:** Reiter **Daten** und Tag/Woche anschauen. Die alte lokale Speicherkennung `gesundheits_tracker_v1` bleibt unverändert. **Nur wenn Einträge fehlen**: Reiter **Daten** → **JSON importieren** → gesicherte v1-Datei wählen. Der Import ersetzt alle gerade vorhandenen Einträge.
7. **Neues v2-Backup** erstellen. Es enthält zusätzlich Messwerte, Aktivitäten und deine Zielwerte.

## Was ist neu?

- Start-Dashboard mit Tageswerten je Bereich, Wochenschnitt, acht Wochen Verlauf, Fortschritt der Wochenziele und regelbasierten Tipps.
- Automatische 0–5-Punkte-Berechnung aus **Schritten, Stiegenrunden, Schlafdauer, Alkoholportionen und Süßigkeitenportionen**. Die restlichen Kriterien bleiben bewusst manuell. Jeder automatisch gesetzte Punktewert kann überschrieben werden.
- Editierbare Wochenziele und Tageshäkchen für Krafttraining, Hometrainer, Qi Gong, Alkohol, Süßigkeiten sowie Liegestütze.
- V2-JSON-Backup und CSV-Export; alte v1-Backups sind importierbar.

## Bewertungsregeln

| Eingabewert | Punkte |
|---|---|
| Schritte | >8000: 5; >7000: 4; >6000: 3; >5000: 2; >4000: 1; sonst: 0 |
| Stiegenrunden | ≥10: 5; 9: 4; 8: 3; 7: 2; 6: 1; darunter: 0 |
| Schlafstunden | ≥8: 5; ≥7,5: 4; ≥7: 3; ≥6: 2; ≥5: 1; darunter: 0 |
| Alkoholportionen | 0: 5; 1: 4; 2: 3; 3: 2; 4: 1; ≥5: 0 |
| Süßigkeitenportionen | 0: 5; 1: 3; 2: 1; ≥3: 0 |

Die Schritte- und Stiegenskala orientiert sich an der alten Excel-App. Die übrigen automatischen Skalen sind **editierbare Vorschläge im Quellcode**, keine medizinisch validierten Grenzwerte. „Portion“ ist eine vereinfachte persönliche Zähleinheit, keine Gramm- oder Standarddrink-Berechnung.

## Historische Daten und Grenzen

- Bei einem normalen Update auf **demselben iPhone**, derselben installierten Home-Bildschirm-App/Website und unveränderter Pages-Adresse werden vorhandene Bewertungen über den bestehenden lokalen Schlüssel geladen. **Vorher trotzdem sichern!**
- Diese öffentliche GitHub-Version enthält **keine** privaten alten Excel-Einträge (`data.js` enthält `{}`). Bestehende lokale Daten werden nicht auf GitHub hochgeladen.
- Alte Bewertungen werden nicht rückwirkend in gemessene Schritte, Alkoholportionen oder Trainingseinheiten umgerechnet. Dafür sind zusätzlich Messwerte oder Tageshäkchen notwendig.
- Die Wochenziele zeigen jeweils die Zahl der Tage mit auswertbaren Angaben an; fehlende Tage werden nicht als nachgewiesene Nichterfüllung ausgegeben. Ein nicht gesetztes Häkchen ist keine eindeutige Aussage, ob etwas stattgefunden hat.
- Keine direkte Garmin-/Apple-Health-Anbindung, keine Push-Erinnerungen und keine iCloud-Synchronisierung.

## Betrieb und Datenschutz

GitHub Pages veröffentlicht **nur** HTML, CSS, JavaScript und Icon. Die App nutzt `localStorage` auf dem iPhone. Wer Website-Daten löscht, ein Gerät wechselt oder den Domainnamen ändert, muss das JSON-Backup wieder importieren. Das GitHub-Repository darf öffentlich sein, **aber private Backup-Dateien dürfen dort nicht abgelegt werden**.
