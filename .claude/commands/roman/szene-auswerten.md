---
description: Veränderungen aus einer Szene extrahieren und eintragen (Pipeline)
argument-hint: [SZ-ID, z.B. SZ-0042]
---

Nimm die Rolle **Charakterentwickler** ein.

**Pflichtlektüre:**
- [[Roman_Split/_system/agenten/charakterentwickler]]
- [[Roman_Split/_system/entscheidungen/ADR-0011-BEZ-lebenszyklus]] – Erstbegegnungs-BEZ als Pflichtschritt
- [[Roman_Split/_system/regeln/szenen-pipeline]]
- [[Roman_Split/commands.md]] Abschnitt `/roman:szene-auswerten`

Extrahiere alle Veränderungen aus der Szene und trage sie ein. Kategorien:
- Charakter (physisch/psychologisch/Status)
- Beziehung (neu oder verändert; Erstbegegnungs-BEZ halbautomatisch anlegen; Valenzwechsel → neuen Eintrag in `valenz_verlauf` anhängen + Valenz-Spalte in Abschnitt-2-Tabelle; bestehende Einträge nie ändern)
- Ort (physisch/atmosphärisch)
- Gegenstand (Zustand/Besitz/Bedeutung)
- Verknüpfungen (neue Verbindungen)
- Wissen (Vorschläge für subjektiven Kanon)

Output: Aktualisierte Entitäts-Dateien + Änderungsprotokoll.

**Szene:** $ARGUMENTS
