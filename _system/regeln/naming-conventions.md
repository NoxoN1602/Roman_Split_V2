---
typ: regel
id: REG-naming
titel: "Namenskonventionen"
version: "2.1"
status: aktiv
siehe_auch:
  - "[[Roman_Split/_system/entscheidungen/ADR-0002-keine-umlaute-dateinamen]]"
  - "[[Roman_Split/_system/entscheidungen/ADR-0003-einheitliche-prefixe-und-dateinamen]]"
  - "[[Roman_Split/_system/entscheidungen/ADR-0010-obsidian-wiki-links-standard-verlinkung]]"
tags:
  - regel
  - namenskonvention
---

# Namenskonventionen

## Allgemeine Regeln

- Kleinbuchstaben, Bindestrich als Worttrenner
- Keine Umlaute: `ae/oe/ue/ss` (siehe [[Roman_Split/_system/entscheidungen/ADR-0002-keine-umlaute-dateinamen]])
- Keine Leerzeichen, keine Sonderzeichen ausser Bindestrich
- Prefixe verwenden Bindestrich (nicht Unterstrich): `CHAR-` nicht `CHAR_`
- Innerhalb der Dateien (Frontmatter, Titel, Inhalt) dürfen Umlaute und Grossbuchstaben verwendet werden

---

## ID-Prefixe (Referenz-IDs im Frontmatter)

> Diese IDs werden im Frontmatter-Feld `doc_id` verwendet und dienen als systemweite Referenz.

| Prefix | Typ | Beispiel |
|---|---|---|
| `CHAR-{vorname-nachname}` | Charakter | `CHAR-laura-ahler` |
| `ORT-{name}` | Ort | `ORT-lauras-zimmer` |
| `GGS-{name}` | Gegenstand | `GGS-pentagramm-armband` |
| `BEZ-{char1}--{char2}` | Beziehung | `BEZ-laura-ahler--marie-kanter` |
| `SZ-{nnnn}` | Szene | `SZ-0001` |
| `PLOT-{name}` | Plot-Strang | `PLOT-verschwinden-marie` |
| `KAN-OBJ-{zeit}-{thema}` | Kanon objektiv | `KAN-OBJ-RT2025-03-15-tatort` |
| `KAN-SUB-{char}-{zeit}-{thema}` | Kanon subjektiv | `KAN-SUB-laura-RT2025-03-15-wissen` |
| `KON-{nnnn}` | Konzeptdokument | `KON-0001` |
| `ADR-{nnnn}` | Architektur-Entscheidung | `ADR-0001` |
| `REG-{name}` | Regel | `REG-naming` |
| `TMPL-{typ}` | Template | `TMPL-charakter` |
| `AGT-{name}` | Agent | `AGT-ghostwriter` |

---

## Dateinamen-Muster (pro Verzeichnis)

### Inhaltsdateien

| Verzeichnis | Muster | Beispiel |
|---|---|---|
| `charaktere/` | `{vorname-nachname}.md` | `laura-ahler.md` |
| `beziehungen/` | `{char1}--{char2}.md` | `laura-ahler--marie-kanter.md` |
| `orte/` | `{ort-name}.md` | `lauras-zimmer.md` |
| `gegenstaende/` | `{gegenstand-name}.md` | `pentagramm-armband.md` |
| `szenen/` | `SZ-{nnnn}-{kurztitel}.md` | `SZ-0001-marie-verschwindet.md` |
| `plot/` | `{strang-name}.md` | `verschwinden-marie.md` |
| `kanon/objektiv/` | `RT{zeit}-{thema}.md` | `RT2025-03-15-tatort-befunde.md` |
| `kanon/subjektiv/{char}/` | `RT{zeit}-{thema}.md` | `RT2025-03-15-wissen-ueber-marie.md` |
| `reihenfolge/` | `{name}.md` | `kapitelplan.md` |

### Systemdateien

| Verzeichnis | Muster | Beispiel |
|---|---|---|
| `_system/templates/` | `TEMPLATE-{typ}.md` | `TEMPLATE-charakter.md` |
| `_system/agenten/` | `{agenten-name}.md` | `ghostwriter.md` |
| `_system/regeln/` | `{regel-name}.md` | `naming-conventions.md` |
| `_system/konzept/` | `KON-{nnnn}-{titel}.md` | `KON-0001-systemkonzept.md` |
| `_system/entscheidungen/` | `ADR-{nnnn}-{titel}.md` | `ADR-0001-kanon-objektiv-subjektiv.md` |

---

## Beziehungsdateien

- Beide Charakternamen alphabetisch sortiert
- Getrennt durch Doppel-Bindestrich `--`
- Beispiel: `anna-berg--karl-mueller.md` (Anna vor Karl)

---

## Romanzeit-Format

- Prefix: `RT` (Romanzeit)
- Format: `RT{jahr}-{monat}-{tag}` mit optionaler Uhrzeit `T{stunde}:{minute}`
- Jahr ist vierstellig
- Beispiel: `RT2025-07-22T14:00` = 22. Juli 2025, 14:00 Uhr
- Bei unbekanntem Tag: `RT2025-07-00`
- Bei unbekanntem Monat: `RT2025-00-00`

---

## Verweise innerhalb von Dokumenten

> Gemäß [[Roman_Split/_system/entscheidungen/ADR-0010-obsidian-wiki-links-standard-verlinkung]].

| Kontext | Format | Beispiel |
|---|---|---|
| Obsidian-Wiki-Link (navigational) | `[[Roman_Split/pfad/dateiname]]` | `[[Roman_Split/charaktere/laura-ahler]]` |
| Frontmatter-Referenz (`betrifft:`, `siehe_auch:`) | `"[[Roman_Split/pfad/dateiname]]"` | `"[[Roman_Split/_system/regeln/kanon-regeln]]"` |
| `doc_id`-Wert (kein Link, nur ID) | Klartext | `CHAR-laura-ahler` |
| ADR-Nummer im Fließtext | Klartext | `gemäß ADR-0003` |
| Verzeichnisreferenz | Backtick | `` `_system/regeln/` `` |
| Dateiname-Muster mit Wildcard | Backtick | `` `{vorname-nachname}.md` `` |

---

## Migrationhinweis

> Bestehende Dokumente, die noch das alte Format verwenden (z.B. `CHAR_FranzAhler`, `LOC_LaurasZimmer`, `REL_LAURA_MARIE`), müssen bei der nächsten Bearbeitung auf das neue Format migriert werden. Siehe [[Roman_Split/_system/entscheidungen/ADR-0003-einheitliche-prefixe-und-dateinamen]].
