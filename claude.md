# Claude Memory – Roman-Autorensystem

> **Zweck:** Permanentes Gedächtnis für alle Entscheidungen rund um das Roman-Autorensystem.
> **Letzte Aktualisierung:** 2026-04-04
> **Hinweis:** Diese Datei wird fortlaufend ergänzt. Claude liest sie zu Beginn jeder Session.

---

## 1. VISION & GRUNDIDEE

Ein agentengestütztes Autorensystem auf Basis von Markdown-Dateien in Obsidian, das eine komplette fiktive Welt modelliert. Der Roman entsteht nicht-linear durch Dialog zwischen Autor (Til) und spezialisierten Agenten. Ein Kanon-System sichert die innere Konsistenz, während der Autor der Inspiration folgt.

**Root-Verzeichnis:** `Roman_Split/` in der Obsidian-Wissensdatenbank (Dropbox-synchronisiert, Git-versioniert).

> ⚠️ **WICHTIG – Datenquellen:** Dokumente auf Google Drive sind für dieses Projekt **NICHT** relevant. Alle projektrelevanten Dateien liegen ausschließlich im Filesystem unter `Roman_Split/`. Claude soll bei der Arbeit an diesem Projekt **niemals** in Google Drive suchen, sondern ausschließlich über den Filesystem-Zugriff auf die Dateien zugreifen. Google Drive enthält ggf. alte Entwürfe oder Vorlagen, die nicht dem aktuellen Stand entsprechen.

---

## 1b. ROMAN-KURZPROFIL

> **Logline:** Ein traumatisierter Journalist, der den Tod seiner Tochter und seiner Frau nie verwunden hat, beginnt eine Mordserie zu recherchieren, die seine Stadt erschüttert. Was er nicht weiß: Er selbst ist der Mörder. Seine Psyche spaltet die Realität – wo er romantische Begegnungen erlebt, hinterlässt er Leichen. Als er sich mit der ermittelnden Kommissarin verbündet und verliebt, jagt er sich selbst in eine Wahrheit, die alles zerstören wird.

> **Prämisse:** Kann ein Mensch schuldig sein, wenn er seine Schuld nicht kennt?

> **Genre:** Psychologischer Thriller

> **Inspirationen:** Angel Heart (Selbstjagd-Prinzip), Shutter Island (unzuverlässiger Erzähler)

> **Methode:** Save the Cat (modifiziert für Anti-Held) + Story Circle (Subplots)

> **Plot-Status:** Stufe 1 (Kern) ✅ + Stufe 2 (Methodik) ✅ – Stufe 3 (Makrostruktur) steht an

### Kernfiguren

| Figur | Rolle | CHAR-Status |
|-------|-------|-------------|
| Johannes Breier | Protagonist, dissoziativer Serienmörder, Journalist | ✅ v0.1 (Entwurf, viele offene Details) |
| Kommissarin (Name offen) | Ermittlerin, romantisches Interesse, entdeckt Wahrheit vor dem Leser | ⬜ noch nicht angelegt |
| Sündenbock (Name offen) | Hauptverdächtiger, Ablenkungsfigur | ⬜ noch nicht angelegt |
| Redaktions-Vertrauter (Name offen) | Johannes' Anker zur Realität | ⬜ noch nicht angelegt |

### Strukturelle Grundentscheidungen

- **Drei Zeitebenen:** Kindheit (Missbrauch/Prolog), Zwischenzeit (Tod Tochter/Frau), Gegenwart (Mordserie)
- **Zwei-Ebenen-Erzählung:** Mordszenen IMMER aus Johannes' subjektiver (romantisierter) Perspektive; alles andere objektiv
- **Leserführung:** Hinweis-/Gegenhinweis-Waage. Leser ahnt zunehmend, weiß bis zum Ende nicht sicher. Sündenbock als plausible Alternative.
- **Kommissarin-Twist:** Erkennt Wahrheit vor dem Leser; verrät es nicht; Leser erfährt es erst durch ihren letzten Akt
- **Enthüllung Tochter/Frau:** Sehr spät (NICHT letztes Drittel – zu früh), zusammen mit finaler Mörder-Auflösung
- **Save the Cat-Modifikationen:** Mitleid statt Sympathie; tragisches Finale statt positiver Transformation; B-Story = Liebe + Nemesis

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
| 0009 | Plotentwicklung | Agenten, 5-Stufen-Workflow, Methodik, Kreativ/Prüf-Trennung |

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
| `gegenstaende/` | `{name}.md` | `lauras-armband.md` |
| `gegenstaende/bilder/` | `{name}.png` | `lauras-armband.png` |
| `szenen/` | `SZ-{nnnn}-{kurztitel}.md` | `SZ-0042-erstes-treffen.md` |
| `_system/agenten/` | `{agentenid}.md` | `plotarchitect.md` |
| `_system/referenz/` | `REF-{methode}.md` | `REF-save-the-cat.md` |
| `plot/` | `plot-{strangname}.md` | `plot-hauptplot.md` |

### Agenten-IDs

Agenten-IDs sind zusammengeschriebene Kleinbuchstaben ohne Bindestriche (ADR-0009, konsistent mit `charakterentwickler`).

---

## 4. VERZEICHNISSTRUKTUR

```
/Roman_Split/
├── claude.md                  # Permanentes Gedächtnis (diese Datei)
├── commands.md                # Befehlsreferenz aller Slash-Befehle
├── _system/
│   ├── agenten/               # Agenten-Definitionen
│   ├── referenz/              # Dramaturgiemodelle (ADR-0009)
│   ├── templates/
│   ├── regeln/
│   ├── konzept/
│   ├── entscheidungen/
│   └── changelog.md
├── plot/                      # Plot-Dokumente + PLOT_WORKING
├── charaktere/
├── beziehungen/
├── orte/
│   └── grundrisse/
├── gegenstaende/
│   └── bilder/
├── kanon/
│   ├── objektiv/
│   └── subjektiv/
├── szenen/
└── reihenfolge/
```

---

## 5. AGENTEN-SYSTEM

### Architekturprinzip: Trennung Kreation / Prüfung (ADR-0009)

Kreativagenten erzeugen Inhalte, Prüfagenten analysieren und kritisieren. Ein Agent übernimmt nie beide Rollen für dasselbe Artefakt.

### Agenten-Übersicht

| Agent-ID | Typ | Rolle | Status |
|----------|-----|-------|--------|
| `charakterentwickler` | Kreativ | Alle Entitätstypen (CHAR, ORT, GGS, BEZ) | ✅ v1.8 |
| `plotarchitect` | Kreativ | Dialogischer Plot-Entwicklungspartner | ✅ v1.0 |
| `sceneideationpartner` | Kreativ | Szenen-Auflösung + Szenenverträge | ✅ v1.0 |
| `plotanalyst` | Prüfung | Strukturanalyse gegen gewähltes Modell | ✅ v1.0 |
| `conflictanalyst` | Prüfung | Spannungs-/Konfliktanalyse | ✅ v1.0 |
| `canonguardian` | Prüfung | Kanon-Konsistenzprüfung | ✅ v1.0 |
| `themenmotivationagent` | Prüfung | Themen-/Motiv-Konsistenz | ⬜ Vorgesehen |

### Agenten-Bewusstsein

Der `plotarchitect` weiß explizit, welche anderen Agenten existieren und schlägt ihren Einsatz aktiv vor. Delegation erfolgt nie automatisch – der Autor entscheidet.

### Kein Orchestrator

Der `00_ORCHESTRATOR` aus der Entwurfsphase entfällt (ADR-0009). Stattdessen: definierte Pipelines + Autor als Steuerer.

---

## 6. PLOT-SYSTEM (ADR-0009)

### Fünf-Stufen-Workflow

1. **Kern** – Logline & Prämisse ✅
2. **Methodik** – Save the Cat (modifiziert) + Story Circle (Subplots) ✅
3. **Makrostruktur** – Akte, Wendepunkte, Schlüsselmomente ⬜ ← nächster Schritt
4. **Sequenzen & Subplots** – Feinauflösung, Nebenhandlungen
5. **Szenen-Outline** – Fertige Szenenfolge → Szenenverträge

Rücksprünge jederzeit möglich. Nicht-linear.

### Dramaturgiemodelle (in `_system/referenz/`)

| Modell | Datei | Kern | Verwendung |
|--------|-------|------|-----------|
| **Save the Cat** | `REF-save-the-cat.md` | 15 Beats, genre-orientiert | **Hauptmodell** |
| Drei-Akt-Struktur | `REF-drei-akt.md` | Klassisch, universell | Nicht gewählt |
| Heldenreise | `REF-heldenreise.md` | Campbell/Vogler, Transformation | Nicht gewählt |
| **Story Circle** | `REF-story-circle.md` | Dan Harmon, 8 Schritte, pragmatisch | **Ergänzend (Subplots)** |

Gewählte Methode = Leitplanke, nicht Korsett. Agent kennt Details, darf begründet abweichen.

### Plot-Dokumente

- **`plot/plot-hauptplot.md`** (+ `plot/plot-{strangname}.md`): Inhalt – Logline, Methode, Beats, Szenenfolge
- **`plot/PLOT_WORKING.md`**: Zustand – aktuelle Stufe, offene Fragen, nächste Schritte. Wird nach jeder Session aktualisiert.

### Slash-Befehle

- `/plot` – Plotentwicklung starten/fortsetzen (plotarchitect)
- `/plot-check` – Plot analysieren (plotanalyst)

### Prüf-Meilensteine

- **Plot-Meilenstein:** plotarchitect schlägt Prüfagenten vor → Autor entscheidet
- **Vor Szenenausarbeitung:** canonguardian prüft Szenenvertrag
- **Nach Szenenausarbeitung:** canonguardian (immer), plotanalyst (immer), conflictanalyst (optional)

---

## 7. KANON-SYSTEM

Siehe `_system/regeln/kanon-regeln.md`. Keine Änderungen.

**Hinweis für diesen Roman:** Das objektiv/subjektiv-System (ADR-0001) ist besonders relevant: Johannes' subjektiver Kanon weicht fundamental vom objektiven Kanon ab (romantisierte Morde vs. tatsächliche Morde). Die Dramatic-Irony-Modellierung ist Kernmechanik des Romans.

---

## 8. SZENEN-WORKFLOW

Siehe `_system/regeln/szenen-pipeline.md` und `_system/regeln/szenen-lebenszyklus.md`. Wird um Plot-bezogene Prüfschritte erweitert (ADR-0009 E10).

---

## 9. TEMPLATES

| Template | Datei | Version | Status |
|----------|-------|---------|--------|
| Charakter | `TEMPLATE-charakter.md` | v1.1 | ✅ Getestet |
| Beziehung | `TEMPLATE-beziehung.md` | v1.1 | ✅ Getestet |
| Ort | `TEMPLATE-ort.md` | v1.3 | ✅ Getestet |
| Gegenstand | `TEMPLATE-gegenstand.md` | v1.3 | ✅ Getestet |
| Plot-Dokument | `TEMPLATE-plot.md` | v1.0 | ✅ Erstellt |
| PLOT_WORKING | `TEMPLATE-plot-working.md` | v1.0 | ✅ Erstellt |
| Szene | `tmpl-szene.md` | – | ⬜ Grundstruktur |
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

### Agenten-Versionen
- Charakterentwickler: **v1.8** (v1.7 + Agenten-Referenzen aktualisiert auf neue IDs)
- Plotarchitect: **v1.0**
- Plotanalyst: **v1.0**
- Conflictanalyst: **v1.0**
- Canonguardian: **v1.0**
- Sceneideationpartner: **v1.0**

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
| Gegenstand: Lauras Armband | 04-04 | ✅ | `gegenstaende/lauras-armband.md` |

---

## 12. OFFENE PUNKTE

### Plot-Entwicklung (aktuell)
- [x] Stufe 1 (Kern): Logline, Prämisse, zentrale Frage ✅
- [x] Stufe 2 (Methodik): Save the Cat + Story Circle ✅
- [ ] **Stufe 3 (Makrostruktur): 15 Beats mit konkreten Inhalten befüllen**
- [x] Johannes Breier als CHAR-Dokument anlegen ✅ (v0.1 Entwurf – Vertiefung nötig)
- [ ] **Johannes Breier vertiefen** (körperliche Details, Trigger, Hobbys, Ticks, exaktes Geburtsdatum)
- [ ] **Kommissarin benennen und als CHAR anlegen** ← nächster Charakter
- [ ] Sündenbock-Charakter entwickeln und als CHAR anlegen
- [ ] Redaktions-Vertrauten entwickeln
- [ ] Trigger-System definieren (Kindheit → Morde)
- [ ] Rolle der Testdaten-Charaktere (Laura, Marie) im fertigen Roman klären

### System-Entwicklung
- [x] ~~**Plot-System aufbauen (ADR-0009)**~~
- [ ] `szenen-pipeline.md` um Plot-Prüfschritte erweitern
- [ ] Kanon- und Szenen-Templates fertigstellen
- [ ] Abschnitt „Sexualität & Beziehungsverhalten" ins Charakter-Template
- [ ] Bestehende Dateien (Laura, Marie, Laura↔Marie) auf neue Nummerierung aktualisieren
- [ ] Bootstrap.md erstellen
- [ ] themenmotivationagent definieren (wenn Bedarf klarer)
- [ ] Ghostwriter-Agent definieren

---

## 13. CHRONOLOGIE

| Datum | Was |
|-------|-----|
| 04-03 | Grundidee, Systemkonzept, Verzeichnisse, ADR-0001–0003, Agenten, CHAR/BEZ-Templates + Tests |
| 04-04 | ORT/GGS-Templates, Charakterentwickler v1.5→v1.7, ADR-0004–0008 |
| 04-04 | Ort-Test Lauras Zimmer, Grundriss-System (.drawio/.drawio.svg), Bilder-System für Gegenstände |
| 04-04 | Gegenstand-Test: Lauras Armband (`gegenstaende/lauras-armband.md`) ✅ |
| 04-04 | `commands.md` erstellt: Befehlsreferenz aller Slash-Befehle (10 Befehle, Charakterentwickler) |
| 04-04 | **ADR-0009: Plotentwicklung** – 5 Agenten erstellt, 4 Methoden-Referenzen, 2 Templates, 12 Befehle |
| 04-04 | Charakterentwickler v1.7→v1.8: Agenten-Referenzen auf neue IDs aktualisiert |
| 04-04 | Vermerk: Google Drive ist NICHT relevant für dieses Projekt – nur Filesystem-Zugriff |
| 04-04 | **Plot Stufe 1 (Kern) abgeschlossen.** Logline, Prämisse, Erzählstruktur, Leserführung (Waage-System), Kommissarin-Twist, Sündenbock-Konzept. `plot-hauptplot.md` + `PLOT_WORKING.md` erstellt. |
| 04-04 | **Plot Stufe 2 (Methodik) abgeschlossen.** Save the Cat (modifiziert) als Hauptmodell, Story Circle für Subplots. Inspirationen: Angel Heart, Shutter Island. |
| 04-04 | **CHAR-johannes-breier v0.1 angelegt.** Erster Entwurf: Körperlich, Beruf, Wertesystem, Selbstbild, Konflikte, Psychologie, Beziehungsachsen, Entwicklungsbogen, stilistische Signatur, Grenzen. Viele Details noch offen (Augenfarbe, Haarfarbe, Stimmlage, Trigger, Hobbys etc.). Vertiefung in nächster Session. |

---

<!-- 
ANWEISUNGEN FÜR CLAUDE:
- Lies diese Datei und commands.md zu Beginn jeder Session.
- **NIEMALS Google Drive durchsuchen** – alle Projektdateien liegen im Filesystem unter Roman_Split/.
- Bei architektonischen Entscheidungen: IMMER ADR erstellen.
- Bei Widersprüchen: claude.md + ADRs gelten.
- Namenskonventionen: ADR-0003 / naming-conventions.md v2.1.
- Agenten-IDs: zusammengeschriebene Kleinbuchstaben ohne Bindestriche (ADR-0009 E1).
- Neue Slash-Befehle: IMMER in commands.md eintragen.
- Kreativ/Prüf-Trennung beachten (ADR-0009 E2).
- Roman-Plot: Lies PLOT_WORKING.md für den aktuellen Stand der Plotentwicklung.
- Dramaturgiemodell: Save the Cat (modifiziert) + Story Circle (Subplots).
-->
