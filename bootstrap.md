# Bootstrap – Roman-Autorensystem

> **Zweck:** Initialisierungsdokument für jeden neuen Chat. Legt fest, welche Dateien Claude zu Beginn jeder Session laden muss, um das vollständige Projektwissen zur Verfügung zu haben.
> **Letzte Aktualisierung:** 2026-04-05
> **Ablageort:** `Roman_Split/bootstrap.md` (Root-Verzeichnis)

---

## Anweisung an Claude

Du arbeitest an einem agentengestützten Roman-Autorensystem. Bevor du irgendetwas anderes tust, **lade alle unten aufgeführten Dateien** mit einem einzigen `filesystem:read_multiple_files`-Aufruf. Antworte dem Autor erst, nachdem du alle Dateien gelesen hast.

> ⚠️ **Datenquelle:** Alle Projektdateien liegen ausschließlich im Filesystem unter `Roman_Split/`. **Niemals Google Drive durchsuchen.**

> ⚠️ **Schreibregel:** `write_file` überschreibt immer den gesamten Dateiinhalt. Niemals Platzhalter wie „[Abschnitt unverändert]" schreiben – immer vollständigen Text.

> ⚠️ **PFLICHT – bootstrap.md aktuell halten:** Immer wenn eine Datei in einem der folgenden Verzeichnisse **neu angelegt oder gelöscht** wird, muss `bootstrap.md` **sofort und im selben Arbeitsschritt** angepasst werden – ohne Ausnahme, ohne Rückfrage:
> - Root-Verzeichnis (`Roman_Split/`)
> - `_system/entscheidungen/`
> - `_system/agenten/`
> - `_system/konzept/`
> - `_system/regeln/`
>
> Neue Datei → in der Pflichtlektüre eintragen. Gelöschte Datei → aus der Pflichtlektüre entfernen. Diese Regel gilt auch dann, wenn nur ein Agent oder nur ein Befehl die Datei erstellt.

---

## Pflichtlektüre beim Session-Start

Lade alle folgenden Dateien mit **einem** `filesystem:read_multiple_files`-Aufruf:

### Root-Verzeichnis

```
Roman_Split/claude.md
Roman_Split/commands.md
```

### _system/entscheidungen (alle ADRs)

```
Roman_Split/_system/entscheidungen/ADR-0001-kanon-objektiv-subjektiv.md
Roman_Split/_system/entscheidungen/ADR-0002-keine-umlaute-dateinamen.md
Roman_Split/_system/entscheidungen/ADR-0003-einheitliche-prefixe-und-dateinamen.md
Roman_Split/_system/entscheidungen/ADR-0004-keine-redundanz-dynamische-daten.md
Roman_Split/_system/entscheidungen/ADR-0005-emotionaler-wert-charakterspezifisch.md
Roman_Split/_system/entscheidungen/ADR-0006-ein-agent-alle-entitaetstypen.md
Roman_Split/_system/entscheidungen/ADR-0007-einheitliche-bekannte-ereignisse.md
Roman_Split/_system/entscheidungen/ADR-0008-grundrisse-drawio-format.md
Roman_Split/_system/entscheidungen/ADR-0009-plotentwicklung-agenten-und-workflow.md
Roman_Split/_system/entscheidungen/ADR-0010-obsidian-wiki-links-standard-verlinkung.md
Roman_Split/_system/entscheidungen/ADR-0011-bez-lebenszyklus-erstbegegnung.md
Roman_Split/_system/entscheidungen/ADR-0012-valenz-verlauf-bez-dateien.md
```

### _system/agenten (alle Agenten-Prompts)

```
Roman_Split/_system/agenten/charakterentwickler.md
Roman_Split/_system/agenten/plotarchitect.md
Roman_Split/_system/agenten/sceneideationpartner.md
Roman_Split/_system/agenten/plotanalyst.md
Roman_Split/_system/agenten/conflictanalyst.md
Roman_Split/_system/agenten/canonguardian.md
```

### _system/konzept

```
Roman_Split/_system/konzept/KON-0001-systemkonzept.md
```

### _system/regeln

```
Roman_Split/_system/regeln/kanon-regeln.md
Roman_Split/_system/regeln/naming-conventions.md
Roman_Split/_system/regeln/szenen-pipeline.md
Roman_Split/_system/regeln/szenen-lebenszyklus.md
```

---

## Vollständiger Pfad (absolut)

Der absolute Basispfad lautet:

```
/Users/tilmannelser/Library/CloudStorage/Dropbox/Mac (2)/Documents/Tils Wissenswelt Online/Roman_Split/
```

Alle oben genannten Pfade sind relativ zu diesem Basispfad. Für `filesystem:read_multiple_files` die vollständigen absoluten Pfade verwenden.

---

## Nach dem Laden

Sobald alle Dateien geladen sind:

1. **Bestätige** dem Autor kurz, dass die Session initialisiert ist (welche Dateien geladen wurden, aktuelle Versionsstände aus `claude.md`).
2. **Frage**, womit der Autor heute arbeiten möchte – oder reagiere auf seine bereits gestellte Frage.
3. **Lade zusätzliche Dateien** nur bei Bedarf (z. B. Plot-Dokumente, Charakter-Dateien), wenn sie für die aktuelle Aufgabe relevant sind.

### Bedingte Zusatzlektüre (nur bei Bedarf)

| Kontext | Zusätzlich laden |
|---------|-----------------|
| Plot-Arbeit | `plot/PLOT_WORKING.md` + `plot/plot-hauptplot.md` |
| Makrostruktur (Stufe 3) | zusätzlich `plot/plot-beats.md` |
| Strukturfragen | `plot/plot-struktur.md` |
| Charakter-Arbeit | `charaktere/{name}.md` + ggf. Beziehungsdateien |
| Szenen-Arbeit | `szenen/SZ-{nnnn}-*.md` + ggf. Kanon-Dateien |

---

## Wichtigste Sofort-Regeln (Kurzfassung)

- **Kein Google Drive** – nur Filesystem
- **Keine Deltas/Platzhalter** – immer vollständigen Dateiinhalt schreiben
- **Neue Slash-Befehle** → immer in `commands.md` eintragen
- **Architektur-Entscheidungen** → immer als ADR dokumentieren
- **Obsidian-Links** → immer `[[Roman_Split/pfad/datei]]` ohne `.md` (ADR-0010)
- **Dateinamen** → Kleinbuchstaben, Bindestrich, keine Umlaute (ADR-0002/0003)
- **claude.md** → nach jeder Session mit neuen Entscheidungen aktualisieren
- **bootstrap.md** → sofort anpassen, wenn Dateien in Root, entscheidungen, agenten, konzept oder regeln angelegt oder gelöscht werden
