---
typ: regel
id: REG-naming
titel: "Namenskonventionen"
status: aktiv
tags:
  - regel
  - namenskonvention
---

# Namenskonventionen

## Dateinamen

- Kleinbuchstaben, Bindestrich als Worttrenner
- Keine Umlaute: `ae/oe/ue/ss` (siehe [[ADR-0002-keine-umlaute-dateinamen]])
- Keine Leerzeichen, keine Sonderzeichen ausser Bindestrich

## ID-Prefixe

| Prefix | Typ | Beispiel |
|---|---|---|
| `SZ-{nnnn}` | Szene | `SZ-0001-der-sturm-bricht-los.md` |
| `CHAR-` | Charakter | `CHAR-maren-steinfeld` (in Frontmatter) |
| `ORT-` | Ort | `ORT-hafen-von-eldara` |
| `GGS-` | Gegenstand | `GGS-kompass-der-gezeiten` |
| `BEZ-` | Beziehung | `BEZ-maren-steinfeld--jonas-krath` |
| `PLOT-` | Plot-Strang | `PLOT-hauptplot` |
| `KAN-OBJ-` | Kanon objektiv | `KAN-OBJ-RT0001-00-00-geographie` |
| `KAN-SUB-` | Kanon subjektiv | `KAN-SUB-maren-RT0003-07-01-wissen` |
| `KON-{nnnn}` | Konzeptdokument | `KON-0001-systemkonzept.md` |
| `ADR-{nnnn}` | Architektur-Entscheidung | `ADR-0001-kanon-objektiv-subjektiv.md` |

## Dateinamen-Muster

| Verzeichnis | Muster | Beispiel |
|---|---|---|
| `szenen/` | `SZ-{nnnn}-{kurztitel}.md` | `SZ-0042-erstes-treffen-am-hafen.md` |
| `charaktere/` | `{vorname-nachname}.md` | `maren-steinfeld.md` |
| `beziehungen/` | `{char1}--{char2}.md` | `maren-steinfeld--jonas-krath.md` |
| `orte/` | `{ort-name}.md` | `hafen-von-eldara.md` |
| `gegenstaende/` | `{gegenstand-name}.md` | `kompass-der-gezeiten.md` |
| `kanon/objektiv/` | `RT{zeit}-{thema}.md` | `RT0001-00-00-eldara-geographie.md` |
| `kanon/subjektiv/{char}/` | `RT{zeit}-{thema}.md` | `RT0003-07-01-wissen-ueber-jonas.md` |
| `plot/` | `{strang-name}.md` | `hauptplot.md` |

## Romanzeit-Format

- Prefix: `RT` (Romanzeit)
- Format: `RT{jahr}-{monat}-{tag}` mit optionaler Uhrzeit `T{stunde}:{minute}`
- Jahr ist vierstellig, beginnt bei `0000` oder `0001` (projektspezifisch)
- Beispiel: `RT0003-07-22T14:00` = Jahr 3, 22. Juli, 14:00 Uhr

## Beziehungsdateien

- Beide Charakternamen alphabetisch sortiert
- Getrennt durch Doppel-Bindestrich `--`
- Beispiel: `anna-berg--karl-mueller.md` (Anna vor Karl)
