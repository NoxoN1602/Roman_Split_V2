---
typ: entscheidung
id: ADR-0010
titel: "Obsidian-Wiki-Links als Standard für interne Verlinkung"
datum: 2026-04-05
status: akzeptiert
betrifft:
  - "[[Roman_Split/_system/regeln/naming-conventions]]"
  - "[[Roman_Split/_system/konzept/KON-0001-systemkonzept]]"
tags:
  - namenskonvention
  - verlinkung
  - obsidian
---

# ADR-0010 – Obsidian-Wiki-Links als Standard für interne Verlinkung

## Kontext

Das Autorensystem besteht aus vielen Markdown-Dateien, die sich gegenseitig referenzieren. Bisher wurden Querverweise auf andere Projektdokumente inkonsistent notiert: teils als Wiki-Links (`[[dateiname]]`), teils als Backtick-formatierter Text (`` `dateiname.md` ``), teils als Klartext. In Obsidian sind Wiki-Links klickbar, ermöglichen Graph View, Backlinks und automatisches Link-Update beim Umbenennen von Dateien.

Zusätzlich wurden Wiki-Links ohne einheitliches Pfad-Schema notiert: Einige nutzten den kurzen Dateinamen (`[[plot-hauptplot]]`), was in einem großen Vault bei Namensgleichheit mit anderen Dateien zu Fehlauflösungen führen kann. Da der Obsidian-Vault bei `Tils Wissenswelt Online/` liegt (nicht bei `Roman_Split/`), soll für maximale Explizitheit und Robustheit – insbesondere für Claude, der die Dateien als Text liest und den Pfad daraus extrahiert – immer der vollständige Pfad vom Vault-Root angegeben werden.

## Entscheidung

### 1. Wiki-Links überall – mit vollständigem Pfad vom Vault-Root

Alle Querverweise auf andere Projektdokumente werden als Obsidian-Wiki-Link mit vollständigem Pfad vom Vault-Root notiert:

```
[[Roman_Split/path/to/dateiname]]
```

**Beispiele:**

| Alt (nicht mehr) | Neu (Standard) |
|------------------|----------------|
| `[[plot-hauptplot]]` | `[[Roman_Split/plot/plot-hauptplot]]` |
| `` `plotarchitect.md` `` | `[[Roman_Split/_system/agenten/plotarchitect]]` |
| `plot-hauptplot.md` (Klartext) | `[[Roman_Split/plot/plot-hauptplot]]` |
| `[[charakterentwickler]]` | `[[Roman_Split/_system/agenten/charakterentwickler]]` |

### 2. Immer ohne `.md`-Extension

Obsidian-Wiki-Links verwenden keine `.md`-Dateiendung:
- ✅ `[[Roman_Split/plot/plot-hauptplot]]`
- ❌ `[[Roman_Split/plot/plot-hauptplot.md]]`

### 3. Display-Text optional

Bei Bedarf kann ein lesbarer Anzeigetext angegeben werden:
`[[Roman_Split/plot/plot-hauptplot|Plot-Hauptplot]]`

### 4. Wo NICHT verlinkt wird

Wiki-Links sind in folgenden Kontexten explizit **nicht** erwünscht:

| Kontext | Format | Beispiel |
|---------|--------|---------|
| Reine Text-Erwähnung ohne Navigationsabsicht | Klartext | `gemäß ADR-0003`, `siehe naming-conventions` |
| Verzeichnisreferenzen (Directories) | Klartext/Backtick | `` `_system/regeln/` ``, `` `kanon/objektiv/` `` |
| Dateinamen-Muster mit Wildcards | Backtick | `` `{vorname-nachname}.md` `` |
| YAML-Code-Blöcke und Frontmatter-Beispiele | Unverändert | `[[placeholder]]` in Code-Fence |
| Template-Platzhalter in Vorlagen-Dateien | Unverändert | `[[{charakter}]]` in Template-Feldern |
| `doc_id`-Felder (IDs, keine Links) | Klartext | `CHAR-laura-ahler` |
| ADR-Nummern in Prosatext | Klartext | `gemäß ADR-0003`, `nach ADR-0009 E1` |

### 5. Frontmatter `betrifft:` und `siehe_auch:`

In Frontmatter-Feldern, die auf andere Dokumente verweisen, werden Wiki-Links mit vollständigem Pfad in Anführungszeichen notiert:

```yaml
betrifft:
  - "[[Roman_Split/_system/regeln/naming-conventions]]"
  - "[[Roman_Split/_system/entscheidungen/ADR-0003-einheitliche-prefixe-und-dateinamen]]"
```

### 6. Noch nicht existierende Dateien

Wiki-Links auf geplante, aber noch nicht existierende Dateien sind erlaubt. Obsidian zeigt sie als unaufgelöste Links. Sie werden bei Datei-Erstellung automatisch aufgelöst:
- `[[Roman_Split/plot/plot-subplots]]` (wird in Stufe 4 angelegt)
- `[[Roman_Split/_system/agenten/themenmotivationagent]]` (noch nicht definiert)

## Konsequenzen

- Alle bestehenden kurzen Wiki-Links (`[[short-link]]`) wurden auf vollständige Pfade aktualisiert
- Bestehende Backtick-Referenzen auf konkrete Projektdateien wurden zu Wiki-Links
- Obsidian zeigt bei allen Links korrekte Backlinks und Graph-View-Verbindungen
- Claude kann Dateipfade direkt aus den Wiki-Links extrahieren, ohne den Vault-Root zu kennen
- Bei Dateien, die noch nicht existieren, kann bereits ein Wiki-Link mit vollständigem Pfad notiert werden

## Alternativen (verworfen)

- **Kurze Wiki-Links ohne Pfad (`[[dateiname]]`):** Funktioniert bei eindeutigen Namen im Vault, aber fragil bei Namenskonflikten; für Claude weniger informativ, da der Pfad nicht ableitbar ist
- **Backtick-formatierter Text weiterhin:** Keine Klickbarkeit, kein Graph View, kein Backlinks-Panel, keine automatischen Link-Updates
- **Relative Pfade statt Vault-Root-Pfade:** Müssten je nach Quelldatei unterschiedlich notiert werden; Vault-Root-Pfade sind kontextunabhängig und einheitlich
