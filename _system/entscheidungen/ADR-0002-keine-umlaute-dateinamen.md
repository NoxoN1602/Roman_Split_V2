---
typ: entscheidung
id: ADR-0002
titel: "ASCII-only Dateinamen, keine Umlaute"
datum: 2026-04-03
status: akzeptiert
betrifft:
  - "[[Roman_Split/_system/konzept/KON-0001-systemkonzept]]"
tags:
  - namenskonvention
  - architektur
---

# ADR-0002 – ASCII-only Dateinamen, keine Umlaute

## Kontext

Das Roman-Projekt liegt in einem Git-Repository. Umlaute in Dateinamen (ae, oe, ue, ss) koennen auf verschiedenen Betriebssystemen und Git-Konfigurationen unterschiedlich behandelt werden (Unicode-Normalisierung NFC vs. NFD, besonders problematisch zwischen macOS und Linux/Windows).

## Entscheidung

Alle Datei- und Verzeichnisnamen verwenden ausschliesslich ASCII-Zeichen:
- `ae` statt `ä`
- `oe` statt `ö`
- `ue` statt `ü`
- `ss` statt `ß`

Dies betrifft NUR Dateinamen. Innerhalb der Dateien (Inhalt, Frontmatter-Werte, Titel) duerfen und sollen Umlaute normal verwendet werden.

**Beispiele:**
- Verzeichnis: `gegenstaende/` (nicht `gegenstände/`)
- Datei: `kanon-waechter.md` (nicht `kanon-wächter.md`)
- Frontmatter: `titel: "Kanon-Wächter"` (Umlaute im Inhalt OK)

## Konsequenzen

- Git-Kompatibilitaet ueber alle Plattformen gesichert
- Obsidian-Wiki-Links muessen die ASCII-Variante verwenden: `[[kanon-waechter]]`
- Leichte kognitive Diskrepanz zwischen Dateiname und Titel im Frontmatter

## Alternativen (verworfen)

- **Umlaute in Dateinamen erlauben** → Git-Probleme bei Cross-Platform-Nutzung, Dropbox-Sync kann NFC/NFD-Probleme verursachen
- **Umlaute komplett vermeiden, auch im Inhalt** → Unnoetig restriktiv, verschlechtert Lesbarkeit
