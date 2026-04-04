---
typ: entscheidung
id: ADR-0003
titel: "Einheitliche Prefixe und Dateinamen für alle Dokumenttypen"
datum: 2026-04-03
status: akzeptiert
betrifft:
  - "[[KON-0001-systemkonzept]]"
  - "[[naming-conventions]]"
  - "[[ADR-0002-keine-umlaute-dateinamen]]"
tags:
  - namenskonvention
  - architektur
---

# ADR-0003 – Einheitliche Prefixe und Dateinamen für alle Dokumenttypen

## Kontext

Im bisherigen Arbeitsprozess haben sich zwei unterschiedliche Konventionen für Prefixe und Referenz-IDs eingeschlichen:

**Alt (inkonsistent):**
- Unterstrich als Trenner: `CHAR_FranzAhler`, `LOC_LaurasZimmer`, `REL_LAURA_MARIE`
- Gemischte Gross-/Kleinschreibung: `FranzAhler` vs. `laura-ahler`
- Unterschiedliche Prefix-Namen: `LOC_` vs. `ORT-`, `REL_` vs. `BEZ-`

**Neu (einheitlich):**
- Bindestrich als Trenner: `CHAR-franz-ahler`, `ORT-lauras-zimmer`, `BEZ-laura-ahler--marie-kanter`
- Durchgehend Kleinschreibung in IDs und Dateinamen
- Konsistente Prefix-Namen über alle Typen hinweg

Zusätzlich fehlten Konventionen für Systemdateien: Templates (`TMPL-`), Agenten (`AGT-`), Regeln (`REG-`).

## Entscheidung

### 1. Alle Prefixe verwenden Bindestrich, nicht Unterstrich

- `CHAR-` statt `CHAR_`
- `ORT-` statt `LOC_`
- `BEZ-` statt `REL_`
- `GGS-` für Gegenstände (neu)

**Begründung:** Bindestrich ist konsistent mit ADR-0002 (ASCII-Dateinamen) und dem Dateisystem-Standard. Unterstrich hat in manchen Kontexten (Markdown, Obsidian) Sonderbedeutung (kursiv).

### 2. Referenz-IDs immer in Kleinschreibung

- `CHAR-laura-ahler` statt `CHAR_LauraAhler`
- Ausnahme: Der Prefix selbst bleibt in Grossbuchstaben (`CHAR-`, `ORT-`, `SZ-`)

**Begründung:** Vermeidet Mehrdeutigkeit bei Gross-/Kleinschreibung. Dateinamen sind ohnehin lowercase (REG-naming), die IDs sollten dazu passen.

### 3. Standardisierte Prefix-Tabelle

| Prefix | Typ | Dateiname-Muster |
|---|---|---|
| `CHAR-` | Charakter | `charaktere/{vorname-nachname}.md` |
| `ORT-` | Ort | `orte/{ort-name}.md` |
| `GGS-` | Gegenstand | `gegenstaende/{name}.md` |
| `BEZ-` | Beziehung | `beziehungen/{char1}--{char2}.md` |
| `SZ-` | Szene | `szenen/SZ-{nnnn}-{kurztitel}.md` |
| `PLOT-` | Plot-Strang | `plot/{strang-name}.md` |
| `KAN-OBJ-` | Kanon objektiv | `kanon/objektiv/RT{zeit}-{thema}.md` |
| `KAN-SUB-` | Kanon subjektiv | `kanon/subjektiv/{char}/RT{zeit}-{thema}.md` |
| `KON-` | Konzept | `_system/konzept/KON-{nnnn}-{titel}.md` |
| `ADR-` | Entscheidung | `_system/entscheidungen/ADR-{nnnn}-{titel}.md` |
| `REG-` | Regel | `_system/regeln/{name}.md` |
| `TMPL-` | Template | `_system/templates/TEMPLATE-{typ}.md` |
| `AGT-` | Agent | `_system/agenten/{name}.md` |

### 4. Migration bestehender Dokumente

Bestehende Dokumente mit altem Format werden bei der nächsten Bearbeitung migriert. Es gibt keine Pflicht zur sofortigen Umbenennung, aber neue Dokumente MÜSSEN das neue Format verwenden.

## Konsequenzen

- Alle Agenten und Templates müssen die neuen Prefixe verwenden
- Bestehende Verweise in Lauras Charakter-Dokument (`CHAR_FranzAhler`, `LOC_LaurasZimmer`, `REL_LAURA_MARIE`) werden beim nächsten Edit angepasst
- Wiki-Links in Obsidian sind nach Migration einheitlich: `[[laura-ahler]]`, `[[lauras-zimmer]]`
- Dataview-Queries können sauber nach `doc_id`-Prefixen filtern

## Alternativen (verworfen)

- **Unterstrich beibehalten:** Inkonsistent mit Dateisystem-Konvention, Sonderbedeutung in Markdown
- **CamelCase in IDs:** Fehleranfällig, nicht einheitlich durchzuhalten
- **Keine Prefixe, nur Verzeichnisse:** Verliert die Eindeutigkeit bei Querverweisen über Verzeichnisgrenzen hinweg
