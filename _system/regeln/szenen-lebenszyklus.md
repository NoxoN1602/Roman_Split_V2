---
typ: regel
id: REG-szenen-lebenszyklus
titel: "Szenen-Lebenszyklus"
version: "1.0"
status: aktiv
siehe_auch:
  - "[[Roman_Split/_system/regeln/szenen-pipeline]]"
  - "[[Roman_Split/_system/regeln/naming-conventions]]"
tags:
  - regel
  - szene
  - workflow
---

# Szenen-Lebenszyklus

## Übersicht

Jede Szene durchläuft einen definierten Lebenszyklus. Der Status steuert, welche Agenten auf die Szene zugreifen dürfen und ob abgeleitete Dokumente (Kanon, Charakter-Updates, Beziehungs-Updates) erzeugt werden.

---

## Status-Definitionen

### entwurf

- **Bedeutung:** Die Szene wird aktiv geschrieben oder überarbeitet.
- **Wer darf schreiben:** Ghostwriter, Autor (manuell)
- **Pipeline:** Nein – keine Auswertung, keine Kanon-Ableitung.
- **Abgeleitete Dokumente:** Keine.
- **Übergang zu:** `abgenommen` (durch explizite Bestätigung des Autors)

### abgenommen

- **Bedeutung:** Die Szene gilt als inhaltlich fertig. Ihr Inhalt ist verbindlich.
- **Wer darf schreiben:** Niemand (gesperrt für inhaltliche Änderungen)
- **Pipeline:** Ja – wird beim Übergang zu diesem Status automatisch ausgelöst.
- **Abgeleitete Dokumente:** Kanon-Einträge, Charakter-Updates, Beziehungs-Updates werden erstellt. Alle abgeleiteten Dokumente referenzieren die Szene und deren Version.
- **Übergang zu:** `revision` (durch expliziten Wunsch des Autors)

### revision

- **Bedeutung:** Die Szene wurde wieder geöffnet. Inhaltliche Änderungen sind erlaubt.
- **Wer darf schreiben:** Ghostwriter, Autor (manuell)
- **Pipeline:** Nein – läuft erst wieder bei erneuter Abnahme.
- **Abgeleitete Dokumente:** Alle aus dieser Szene abgeleiteten Einträge werden als `⚠️ potenziell veraltet (Szene in Revision)` geflaggt. Sie werden nicht gelöscht, aber sichtbar markiert.
- **Übergang zu:** `abgenommen` (erneute Bestätigung, Version wird hochgezählt)

### archiviert

- **Bedeutung:** Die Szene wurde verworfen oder durch eine andere ersetzt.
- **Wer darf schreiben:** Niemand
- **Pipeline:** Nein
- **Abgeleitete Dokumente:** Alle Ableitungen dieser Szene werden überprüft. Falls sie ausschließlich auf dieser Szene basieren, werden sie als `veraltet` markiert.
- **Übergang zu:** Kein regulärer Übergang. Reaktivierung nur durch manuelle Entscheidung.

---

## Status-Übergänge (Diagramm)

```
                    Autor: "Ja, abnehmen"
  ┌──────────┐    ──────────────────────►    ┌─────────────┐
  │  entwurf │                               │ abgenommen  │
  └──────────┘    ◄──────────────────────    └─────────────┘
                    Autor: "Wieder öffnen"          │
                    → Status: revision              │
                                                    │
                  ┌──────────┐                      │
                  │ revision │ ─────────────────────┘
                  └──────────┘   Autor: "Erneut abnehmen"
                       │          → Version +1, Pipeline erneut
                       │
                       ▼
                  ┌────────────┐
                  │ archiviert │
                  └────────────┘
```

---

## Frontmatter-Felder für Szenen

```yaml
status: entwurf # entwurf | abgenommen | revision | archiviert
version: "1.0"  # Wird bei erneuter Abnahme hochgezählt (1.0 → 2.0)
abgenommen_am: "" # Datum der letzten Abnahme
revision_grund: "" # Warum wurde die Szene wieder geöffnet?
```

---

## Regeln

1. **Keine Pipeline ohne Abnahme.** Solange eine Szene den Status `entwurf` oder `revision` hat, werden keine Kanon-Einträge oder Charakter-Updates abgeleitet.
2. **Keine Änderung ohne Revision.** Eine abgenommene Szene darf nicht direkt bearbeitet werden. Der Status muss zuerst auf `revision` gesetzt werden.
3. **Flagging statt Löschen.** Bei einer Revision werden abgeleitete Dokumente markiert, nicht gelöscht. Erst nach erneuter Abnahme werden sie aktualisiert oder bestätigt.
4. **Versionierung ist Pflicht.** Jede erneute Abnahme erhöht die Versionsnummer. Abgeleitete Dokumente referenzieren immer die konkrete Version.
5. **Revision braucht Begründung.** Das Feld `revision_grund` muss befüllt werden, damit nachvollziehbar ist, warum eine abgenommene Szene wieder geöffnet wurde.
