# Mein Gesundheits-Tracker 3.0 – Update für GitHub Pages

## Was neu ist
- **Analyse**: Tage (28 Tage), Wochen (12 Wochen), Monate (12 Monate) mit Zeitraum-Navigation, Bereich und allen **14 Einzelkriterien** sowie Gruppen- und Gesamtbewertung. Diagramm mit fehlenden Daten als Lücken; Zielwert-Linie, Verteilung und 28-Tage-Vergleich.
- **Persönliche Ziele**: 0 bis 5 Punkte je Unterkriterium, Bereich und Gesamtwert. Voreinstellung 4,0. Die alten wöchentlichen Aktivitätsziele bleiben unverändert.
- **Maßnahmen**: Freitext-Maßnahme, Startdatum, zugeordnetes Kriterium, Status (geplant / aktiv / abgeschlossen / nicht wirksam).
- **Monatsreview**: Bereichsergebnisse gegenüber dem Vormonat, Verbesserungsfelder, positive Entwicklungen und laufende Maßnahmen. Eine Bewertung ist kein klinischer Gesundheitswert.
- **V3-Backup**: Vollständiges JSON mit allen alten Daten, Messwerten, Wochenzielen, neuen Zielwerten und Maßnahmen. Import von v1, v2 und v3 möglich.

## Update auf GitHub und Daten behalten (Reihenfolge wichtig)

1. Auf dem **iPhone** die bisherige App öffnen: **Daten → Vollständiges Backup (JSON)**. Sicherung in "Dateien" oder iCloud Drive ablegen und kontrollieren, dass die `.json`-Datei existiert. **Nicht** zu GitHub hochladen.
2. **GitHub** im bestehenden Repository `gesundheits-tracker` öffnen → **Add file → Upload files**. Die **entpackten acht App-Dateien** aus diesem ZIP hochladen: `index.html`, `style.css`, `app.js`, `v3.js` (neu), `sw.js`, `data.js`, `manifest.webmanifest`, `icon.svg`. `README.md` ist optional. Gleichnamige Dateien im Hauptverzeichnis ersetzen.
3. **Commit changes** anklicken. Unter **Settings → Pages** die bisherigen Einstellungen `Deploy from a branch`, `main`, `/(root)` beibehalten.
4. Auf dem iPhone die **bestehende GitHub-Pages-Adresse** in Safari neu öffnen, neu laden; die installierte Web-App erneut öffnen. Möglicherweise alte App schließen und neu starten, weil Offline-Cache aktualisiert wird. **Nicht die App vor der Sicherung löschen.**
5. In **Daten** die Anzahl der Bewertungstage und vorhandene Tageseinträge kontrollieren. Die bisherige lokale Speicherkennung `gesundheits_tracker_v1` sowie `gesundheits_tracker_v2_extra` und `gesundheits_tracker_v2_goals` bleibt identisch – bei unveränderter URL und Browserumgebung bleiben die Daten normalerweise erhalten.
6. **Nur wenn wirklich erforderlich**, gesichertes JSON unter **Daten → JSON importieren** auswählen. Achtung: Import ersetzt ALLE aktuell lokal gespeicherten Daten, auch Maßnahmen und Zielwerte. Vor einem Import immer den aktuellen Stand separat sichern.
7. Nun unter **Daten → Vollständiges JSON-Backup** eine aktuelle V3-Sicherung erstellen.

## Daten und Auswertung
- Die 14 bekannten Kriterien und ihre bisherigen täglichen Werte (0–5) werden nicht geändert oder rückwirkend neu berechnet. Die bestehenden Regeln für automatische Punkte in V2 bleiben unverändert.
- Tage mit fehlenden Einträgen werden nicht als 0 gewertet. Wochen beginnen am **Montag**. Zeiträume können aktuell auch Teilzeiträume enthalten; ihre Eintragsanzahl wird angezeigt.
- Ein Gesamt-/Gruppentageswert ist das Mittel der **an diesem Tag erfassten** Kriterien; die individuelle Trendansicht berechnet anschließend den Durchschnitt der vorhandenen Tageswerte je Woche/Monat. Daher können Tage mit unvollständigen Bewertungen den Durchschnitt beeinflussen.
- Tage mit null Einträgen erscheinen in der Analyse als Lücke. Wochen-/Monatswerte zeigen nur vorhandene Bewertungen. Für historische Daten sind keine Rückschlüsse auf nicht separat erfasste Aktivitäten möglich.
- 28-Tage-Vergleich und Monatsreview sind **deskriptiv**, keine medizinischen Empfehlungen oder Kausalnachweise. Insbesondere ist „Stress“ die subjektive 0–5-Schlafbewertung, kein medizinischer Stresswert.

## Sicherheit & Betrieb
- **Kein Konto, keine Cloud-Datenbank, keine automatische Synchronisierung.** Gesundheitsdaten liegen im lokalen `localStorage` der Web-App auf dem jeweiligen Gerät.
- GitHub speichert nur die veröffentlichten App-Dateien. Private JSON-Backups gehören ausschließlich in private Ablagen, niemals ins öffentliche GitHub-Repository.
- Regelmäßige JSON-Backups machen; Websitedaten löschen, Domainwechsel oder iPhone-Wechsel können die lokalen Daten sonst beseitigen.
- App-Dateien sind bewusst ohne externe JavaScript-Bibliotheken gehalten und nach dem ersten Laden grundsätzlich offline nutzbar; GitHub Pages benötigt für Updates eine Internetverbindung.
