---
typ: entscheidung
id: ADR-0008
titel: "Visuelle Referenzen für Orte und Gegenstände"
datum: 2026-04-04
status: akzeptiert
betrifft:
  - "[[TEMPLATE-ort]]"
  - "[[TEMPLATE-gegenstand]]"
  - "[[charakterentwickler]]"
  - "[[naming-conventions]]"
tags:
  - architektur
  - ort
  - gegenstand
  - visualisierung
---

# ADR-0008 – Visuelle Referenzen für Orte und Gegenstände

## Kontext

Beim Schreiben von Szenen müssen räumliche Verhältnisse und das Aussehen von Gegenständen stimmen. Textuelle Beschreibungen allein sind fehleranfällig – der Ghostwriter kann räumliche Fehler machen oder Gegenstände inkonsistent beschreiben. Visuelle Referenzen direkt in den Entitäts-Dokumenten lösen dieses Problem.

## Entscheidung

Orte und Gegenstände erhalten optionale visuelle Referenzen in Abschnitt 0 ihres jeweiligen Templates, direkt oben im Dokument, vor Rolle & Funktion. Die visuellen Referenzen sind KANN-Elemente.

### A) Grundrisse für Orte

**Doppeldatei** in `orte/grundrisse/`:
- `.drawio` – Editierbare Quelldatei (draw.io Desktop). Jedes Möbelstück ein einzeln verschiebbares Objekt.
- `.drawio.svg` – SVG-Export aus draw.io (Anzeige in Obsidian). Draw.io erzeugt diese Endung automatisch.

**Namenskonvention:** `{ort-name}.drawio` + `{ort-name}.drawio.svg`

**Integration:**
- Frontmatter: `grundriss: "grundrisse/{ort-name}.drawio"` (Quelle)
- Abschnitt 0: `![[grundrisse/{ort-name}.drawio.svg]]` (Anzeige)

**Workflow:** Claude generiert `.drawio` → Autor verfeinert in draw.io → Autor exportiert als SVG → Obsidian zeigt an.

### B) Bilder für Gegenstände

**Einzeldatei** in `gegenstaende/bilder/`:
- `.png` – Bilddatei des Gegenstands. Obsidian rendert PNGs nativ.

**Namenskonvention:** `{gegenstand-name}.png`

**Integration:**
- Frontmatter: `bild: "bilder/{gegenstand-name}.png"`
- Abschnitt 0: `![[bilder/{gegenstand-name}.png]]`

**Workflow:** Der Autor erstellt oder beschafft ein Bild extern und legt es im Verzeichnis ab. Der Agent kann keine fotorealistischen Bilder generieren und weist stattdessen darauf hin, dass der Autor ein Bild manuell ablegen kann.

### Gemeinsame Prinzipien

- Abschnitt 0 wird bei der Erstellung automatisch mit dem Einbettungslink befüllt, auch wenn die Datei noch nicht existiert.
- Der Agent weist am Ende der Erstellung auf die Möglichkeit hin.
- `/check` prüft, ob die referenzierten visuellen Dateien existieren, und gibt einen 💡-Hinweis, wenn nicht (kein Fehler, nur Vorschlag).

## Konsequenzen

- Räumliche und visuelle Konsistenz wird prüfbar
- Der Ghostwriter hat beim Schreiben eine visuelle Referenz
- Grundrisse: Zwei Dateien pro Ort (Quelle + Export); nach jeder Bearbeitung SVG neu exportieren
- Bilder: Eine Datei pro Gegenstand; muss extern erstellt werden
- Obsidian zeigt beides nativ an (SVG und PNG), kein Plugin nötig

## Alternativen (verworfen)

- **Nur `.drawio` ohne SVG-Export:** Obsidian kann reines draw.io-XML nicht rendern.
- **Nur SVG für Grundrisse:** Nicht editierbar in draw.io.
- **Agent generiert fotorealistische Bilder:** Technisch nicht möglich; Agent kann nur schematische SVGs erstellen.
- **Keine visuellen Referenzen:** Räumliche/visuelle Fehler beim Schreiben sind wahrscheinlich.
