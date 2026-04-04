# Claude Memory – Roman-Autorensystem

> **Zweck:** Permanentes Gedächtnis für alle Entscheidungen rund um das Roman-Autorensystem.
> **Letzte Aktualisierung:** 2026-04-04
> **Hinweis:** Diese Datei wird fortlaufend ergänzt. Claude liest sie zu Beginn jeder Session.

---

## 1. VISION & GRUNDIDEE

Ein agentengestütztes Autorensystem auf Basis von Markdown-Dateien in Obsidian, das eine komplette fiktive Welt modelliert. Der Roman entsteht nicht-linear durch Dialog zwischen Autor (Til) und spezialisierten Agenten. Ein Kanon-System sichert die innere Konsistenz, während der Autor der Inspiration folgt.

**Root-Verzeichnis:** `Roman_Split/` in der Obsidian-Wissensdatenbank (Dropbox-synchronisiert, Git-versioniert).

---

## 2. ARCHITEKTUR-ENTSCHEIDUNGEN (Kurzreferenz)

> ⚠️ **Pflicht:** Jede architektonische Entscheidung wird als ADR in `_system/entscheidungen/` dokumentiert.

| ADR | Titel | Kern |
|-----|-------|------|
| 0001 | Kanon objektiv/subjektiv | Zwei Verzeichnisse, Dramatic Irony modellierbar |
| 0002 | ASCII-only Dateinamen | `ae/oe/ue/ss`, Git-/Dropbox-Kompatibilität |
| 0003 | Namenskonventionen v2.0 | Bindestrich-Kleinschreibung, standardisierte Prefixe |
| 0004 | Keine Redundanz | Aktueller Stand = letzter Zeitleisten-Eintrag |
| 0005 | Emotionaler Wert dynamisch | In BEZ-Dateien, nicht im Gegenstand |
| 0006 | Ein Agent für alle Typen | Charakterentwickler verwaltet CHAR, ORT, GGS, BEZ |
| 0007 | Einheitliche Ereignisse | KANN-Abschnitt „Bekannte Ereignisse" in allen Templates |
| 0008 | Visuelle Referenzen | Grundrisse (.drawio/.drawio.svg) für Orte, Bilder (.png) für Gegenstände |

---

## 3. NAMENSKONVENTIONEN (naming-conventions.md v2.0)

Kleinbuchstaben, Bindestrich, keine Umlaute in Dateinamen.

### Dateinamen-Muster

| Verzeichnis | Muster | Beispiel |
|-------------|--------|----------|
| `charaktere/` | `{vorname-nachname}.md` | `laura-ahler.md` |
| `beziehungen/` | `{char1}--{char2}.md` | `laura-ahler--marie-kanter.md` |
| `orte/` | `{ort-name}.md` | `lauras-zimmer.md` |
| `orte/grundrisse/` | `{ort-name}.drawio` + `.drawio.svg` | `lauras-zimmer.drawio` |
| `gegenstaende/` | `{name}.md` | `pentagramm-armband.md` |
| `gegenstaende/bilder/` | `{name}.png` | `pentagramm-armband.png` |
| `szenen/` | `SZ-{nnnn}-{kurztitel}.md` | `SZ-0042-erstes-treffen.md` |

---

## 4. VERZEICHNISSTRUKTUR

```
/Roman_Split/
├── claude.md                  # Permanentes Gedächtnis (diese Datei)
├── commands.md                # Befehlsreferenz aller Slash-Befehle
├── _system/
│   ├── agenten/
│   ├── templates/
│   ├── regeln/
│   ├── konzept/
│   ├── entscheidungen/
│   └── changelog.md
├── plot/
├── charaktere/
├── beziehungen/
├── orte/
│   └── grundrisse/          # .drawio + .drawio.svg → ADR-0008
├── gegenstaende/
│   └── bilder/               # .png → ADR-0008
├── kanon/
│   ├── objektiv/
│   └── subjektiv/
├── szenen/
└── reihenfolge/
```

---

## 5–8. KANON, AGENTEN, WORKFLOW, DOKUMENTATION

Siehe vorherige Abschnitte (keine Änderungen). Kanon-System, Agenten-Pipeline, Szenen-Workflow und Dokumentationsprinzipien unverändert.

---

## 9. TEMPLATES

| Template | Datei | Version | Status |
|----------|-------|---------|--------|
| Charakter | `TEMPLATE-charakter.md` | v1.1 | ✅ Getestet |
| Beziehung | `TEMPLATE-beziehung.md` | v1.1 | ✅ Getestet |
| Ort | `TEMPLATE-ort.md` | v1.3 | ✅ Getestet |
| Gegenstand | `TEMPLATE-gegenstand.md` | v1.3 | ✅ Erstellt |
| Szene | `tmpl-szene.md` | – | ⬜ Grundstruktur |
| Plot-Strang | `tmpl-plot-strang.md` | – | ⬜ Offen |
| Kanon | `tmpl-kanon-*.md` | – | ⬜ Offen |

### Übergreifende Prinzipien
- Verknüpfungsmatrix: CHAR↔ORT↔GGS↔BEZ↔PLOT↔SZ
- Keine Redundanz (ADR-0004), emotionaler Wert dynamisch (ADR-0005), einheitliche Ereignisse (ADR-0007)
- **Visuelle Referenzen (ADR-0008):** Orte haben Abschnitt 0 mit Grundriss (`.drawio.svg`), Gegenstände haben Abschnitt 0 mit Bild (`.png`). Links werden bei Erstellung automatisch eingefügt.

### Template-Strukturen
- **Charakter v1.1:** 16 Abschnitte (MUSS 1–10, KANN 11–16)
- **Beziehung v1.1:** 10 Abschnitte (MUSS 1–5, KANN 6–10)
- **Ort v1.3:** Abschnitt 0 = Grundriss, dann 10 Abschnitte (MUSS 1–6, KANN 7–10). Frontmatter: `grundriss:`
- **Gegenstand v1.3:** Abschnitt 0 = Bild, dann 10 Abschnitte (MUSS 1–6, KANN 7–10). Frontmatter: `bild:`

### Agenten-Version
- Charakterentwickler: **v1.7** (inkl. Grundriss-Angebot für Orte, Bild-Hinweis für Gegenstände, `/check` mit visueller Prüfung)

---

## 10. BOOTSTRAP-KONZEPT (noch nicht erstellt)

`bootstrap.md` geplant: Initialisierungsanweisung + Pfad-Konfiguration + Kurzreferenz.

---

## 11. TESTRESULTATE

| Test | Datum | Status | Datei(en) |
|------|-------|--------|-----------|
| Charakter: Laura Ahler | 04-03 | ✅ | `charaktere/laura-ahler.md` |
| Charakter: Marie Kanter | 04-03 | ✅ | `charaktere/marie-kanter.md` |
| Beziehung: Laura↔Marie | 04-03 | ✅ | `beziehungen/laura-ahler--marie-kanter.md` |
| Ort: Lauras Zimmer | 04-04 | ✅ | `orte/lauras-zimmer.md` + `grundrisse/lauras-zimmer.drawio` |
| Gegenstand | – | ⬜ | (Pentagramm-Armband geplant) |

---

## 12. OFFENE PUNKTE

- [ ] Plot-Strang-, Kanon- und Szenen-Templates fertigstellen
- [ ] Abschnitt „Sexualität & Beziehungsverhalten" ins Charakter-Template
- [ ] Bestehende Dateien (Laura, Marie, Laura↔Marie) auf neue Nummerierung aktualisieren
- [ ] Gegenstand-Template testen (Pentagramm-Armband)
- [ ] Bootstrap.md erstellen
- [ ] Agenten-Prompts vervollständigen

---

## 13. CHRONOLOGIE

| Datum | Was |
|-------|-----|
| 04-03 | Grundidee, Systemkonzept, Verzeichnisse, ADR-0001–0003, Agenten, CHAR/BEZ-Templates + Tests |
| 04-04 | ORT/GGS-Templates, Charakterentwickler v1.5→v1.7, ADR-0004–0008 |
| 04-04 | Ort-Test Lauras Zimmer, Grundriss-System (.drawio/.drawio.svg), Bilder-System für Gegenstände |
| 04-04 | `commands.md` erstellt: Befehlsreferenz aller Slash-Befehle (10 Befehle, Charakterentwickler) |

---

<!-- 
ANWEISUNGEN FÜR CLAUDE:
- Lies diese Datei und commands.md zu Beginn jeder Session.
- Bei architektonischen Entscheidungen: IMMER ADR erstellen.
- Bei Widersprüchen: claude.md + ADRs gelten.
- Namenskonventionen: ADR-0003 / naming-conventions.md v2.1.
- Neue Slash-Befehle: IMMER in commands.md eintragen.
-->
