# Befehlsreferenz – Roman-Autorensystem

> **Zweck:** Vollständige Liste aller verfügbaren Slash-Befehle.
> **Letzte Aktualisierung:** 2026-04-19
> **Hinweis:** Diese Datei wird bei jedem neuen Befehl aktualisiert. Claude liest sie zu Beginn jeder Session.
>
> **Ausführung in Claude Code:** Alle Befehle sind als native Slash-Commands unter `.claude/commands/roman/` hinterlegt. Autocomplete mit `/roman` zeigt alle verfügbaren Unterbefehle. Die Command-Dateien sind schlank und verweisen auf den jeweiligen Agenten-Prompt und den passenden Abschnitt in dieser Referenz – operative Details bleiben also hier zentral dokumentiert. **Neue Commands:** Immer beide Orte pflegen (`commands.md` + `.claude/commands/roman/{name}.md`).

---

## Übersicht

| Nr. | Befehl | Agent | Typ | Kurzbeschreibung |
| --- | ------ | ----- | --- | ---------------- |
| 1 | `/roman:neuer-charakter` | Charakterentwickler | Erstellen | Neuen Charakter anlegen (3-Phasen-Workflow) |
| 2 | `/roman:charakter-erweitern [Name]` | Charakterentwickler | Vertiefen | Bestehenden Charakter abschnittsweise vertiefen |
| 3 | `/roman:ort [Name] [Charakter?]` | Charakterentwickler | Erstellen | Neues Ortsdokument anlegen |
| 4 | `/roman:ort-erweitern [Name]` | Charakterentwickler | Vertiefen | Bestehenden Ort abschnittsweise vertiefen |
| 5 | `/roman:gegenstand [Name] [Charakter?]` | Charakterentwickler | Erstellen | Neues Gegenstandsdokument anlegen |
| 6 | `/roman:gegenstand-erweitern [Name]` | Charakterentwickler | Vertiefen | Bestehenden Gegenstand abschnittsweise vertiefen |
| 7 | `/roman:beziehung [A] [B]` | Charakterentwickler | Erstellen | Neue Beziehung zwischen zwei Entitäten anlegen |
| 8 | `/roman:beziehung-aktualisieren [A] [B]` | Charakterentwickler | Aktualisieren | Bestehende Beziehung manuell aktualisieren |
| 9 | `/roman:check [Name]` | Charakterentwickler | Prüfen | Vollständigkeit und Konsistenz prüfen (alle Typen) |
| 10 | `/roman:szene-auswerten [SZ-ID]` | Charakterentwickler | Pipeline | Veränderungen aus Szene extrahieren und eintragen |
| 11 | `/roman:plot` | Plotarchitect | Kreativ | Plotentwicklung starten oder fortsetzen |
| 12 | `/roman:plot-check` | Plotanalyst | Prüfung | Plot gegen gewähltes Modell analysieren |
| 13 | `/roman:canon-check [scope]` | Canonguardian | Prüfung | Kanon-Konsistenzcheck für geänderte Dateien (Session-Ende, Kontextwechsel) |

---

## Befehle im Detail

### /roman:neuer-charakter

> Erstellt einen neuen Charakter in drei Phasen.

- **Agent:** Charakterentwickler
- **Parameter:** keine
- **Workflow:**
  1. **Phase 1 – Freies Erzählen:** Der Agent lässt den Autor frei erzählen, stellt danach 3–5 gezielte Nachfragen.
  2. **Phase 2 – Erster Entwurf:** Mapping auf [[Roman_Split/_system/templates/TEMPLATE-charakter]], Datei unter `charaktere/{vorname-nachname}.md`. Zusammenfassung in: Eingetragen / Abgeleitet / Noch offen.
  3. **Phase 3 – Vertiefung (optional):** Kann sofort oder später via `/roman:charakter-erweitern` erfolgen.
- **Output:** Charakter-Datei (Status: ENTWURF)

---

### /roman:charakter-erweitern [Name]

> Vertieft einen bestehenden Charakter Abschnitt für Abschnitt.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Charakters (z.B. `Laura Ahler`)
- **Ablauf:** Agent öffnet Datei → zeigt offene MUSS-Abschnitte → Autor wählt Abschnitt → gezielte Fragen & Vorschläge → Eintragen → nächster Abschnitt. Nach MUSS optional KANN.
- **Output:** Aktualisierte Charakter-Datei

---

### /roman:ort [Name] [Charakter?]

> Erstellt ein neues Ortsdokument in drei Phasen.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Orts, `[Charakter]` – optional, verknüpfter Charakter
- **Workflow:** Identisch zum Charakter-Workflow (3 Phasen), aber mit ortsspezifischen Fragen (Raumgefühl, Sensorik, Atmosphäre, Funktion im Roman).
- **Template:** [[Roman_Split/_system/templates/TEMPLATE-ort]]
- **Output:** Ort-Datei unter `orte/{ort-name}.md` (Status: ENTWURF)

---

### /roman:ort-erweitern [Name]

> Vertieft einen bestehenden Ort abschnittsweise.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Orts
- **Ablauf:** Wie `/roman:charakter-erweitern`, aber mit ortsspezifischen Fragen (Licht, Zustand, Sensorische Signatur, Atmosphäre).
- **Output:** Aktualisierte Ort-Datei

---

### /roman:gegenstand [Name] [Charakter?]

> Erstellt ein neues Gegenstandsdokument in drei Phasen.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Gegenstands, `[Charakter]` – optional, verknüpfter Charakter
- **Workflow:** Identisch zum Charakter-Workflow (3 Phasen), aber mit gegenstandsspezifischen Fragen (Material, Herkunft, Besitz, Symbolik).
- **Template:** [[Roman_Split/_system/templates/TEMPLATE-gegenstand]]
- **Output:** Gegenstands-Datei unter `gegenstaende/{gegenstand-name}.md` (Status: ENTWURF)

---

### /roman:gegenstand-erweitern [Name]

> Vertieft einen bestehenden Gegenstand abschnittsweise.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Gegenstands
- **Ablauf:** Wie `/roman:charakter-erweitern`, aber mit gegenstandsspezifischen Fragen (Physische Beschreibung, Herkunft, Symbolik, Grenzen).
- **Output:** Aktualisierte Gegenstands-Datei

---

### /roman:beziehung [A] [B]

> Legt eine neue Beziehung zwischen zwei Entitäten an.

- **Agent:** Charakterentwickler
- **Parameter:** `[A]` und `[B]` – Namen der beteiligten Entitäten (Charaktere, Orte oder Gegenstände)
- **Workflow:** 3-Phasen-Workflow mit beziehungsspezifischen Fragen (Art der Beziehung, Dynamik, subjektive Sichten beider Seiten, Konfliktpotenzial).
- **Template:** [[Roman_Split/_system/templates/TEMPLATE-beziehung]]
- **Output:** Beziehungs-Datei unter `beziehungen/{a}--{b}.md` (Status: ENTWURF)

---

### /roman:beziehung-aktualisieren [A] [B]

> Aktualisiert eine bestehende Beziehung manuell.

- **Agent:** Charakterentwickler
- **Parameter:** `[A]` und `[B]` – Namen der beteiligten Entitäten
- **Ablauf:** Agent öffnet BEZ-Datei → zeigt aktuellen Status (letzter Zeitleisten-Eintrag, subjektive Sichten) → fragt nach Veränderung und Auslöser (Szene oder Entwicklung zwischen Szenen) → neuer Zeitleisten-Eintrag.
- **Output:** Aktualisierte Beziehungs-Datei

---

### /roman:check [Name]

> Prüft Vollständigkeit und Konsistenz eines Dokuments (generisch für alle Entitätstypen).

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name der Entität (Charakter, Ort oder Gegenstand)
- **Erkennung:** Agent erkennt den Typ anhand des `doc_type` im Frontmatter
- **Gemeinsame Prüfpunkte:** Vollständigkeit, Verknüpfungen, Kanon-Abgleich, Szenen-Abdeckung, Bekannte Ereignisse
- **Typspezifische Prüfpunkte:**
  - Charakter: Konsistenz (Werte vs. Verhalten, Selbstbild vs. Handlung)
  - Ort: Ort-Hierarchie (übergeordnete/untergeordnete Orte)
  - Gegenstand: Besitz-Tracking-Lücken
- **Output:** Prüfbericht mit Status und Handlungsempfehlungen

---

### /roman:szene-auswerten [SZ-ID]

> Extrahiert alle relevanten Veränderungen aus einer abgenommenen Szene und trägt sie in die betroffenen Dokumente ein.

- **Agent:** Charakterentwickler
- **Parameter:** `[SZ-ID]` – ID der Szene (z.B. `SZ-0001`)
- **Aufruf:** Manuell durch den Autor **oder** automatisch als Pipeline-Schritt 2
- **Kategorien der Extraktion:**
  - Charakter: Physische, psychologische und Status-Änderungen
  - Beziehung: Neue oder veränderte Beziehungen
  - Ort: Physische und atmosphärische Veränderungen
  - Gegenstand: Zustands-, Besitz- und Bedeutungsveränderungen
  - Verknüpfungen: Neue Verbindungen zwischen Entitäten
  - Wissen: Vorschläge für subjektive Kanon-Einträge
- **Output:** Aktualisierte Entitäts-Dateien + Änderungsprotokoll

---

### /roman:plot

> Startet oder setzt die Plotentwicklung fort. Auch über freie Ansprache aufrufbar (z.B. „Lass uns über den Plot reden").

- **Agent:** Plotarchitect
- **Parameter:** keine
- **Zustandserkennung:** Agent liest [[Roman_Split/plot/PLOT_WORKING]] und erkennt den aktuellen Stand automatisch.
- **Erster Aufruf:** Startet bei Stufe 1 (Kern/Logline). Agent fragt nach der Grundidee.
- **Folgende Aufrufe:** Agent meldet den Stand und bietet an, dort weiterzumachen oder etwas anderes aufzugreifen.
- **Workflow (5 Stufen):**
  1. **Kern** – Logline & Prämisse erarbeiten
  2. **Methodik** – Dramaturgiemodell wählen oder ablehnen
  3. **Makrostruktur** – Akte, Wendepunkte, Schlüsselmomente
  4. **Sequenzen & Subplots** – Feinauflösung, Nebenhandlungen
  5. **Szenen-Outline** – Fertige Szenenfolge
- **Output:** [[Roman_Split/plot/plot-hauptplot]] (oder `plot/plot-{strangname}.md`) + [[Roman_Split/plot/PLOT_WORKING]]
- **Session-Ende:** Agent aktualisiert PLOT_WORKING mit aktuellem Stand, offenen Fragen, nächsten Schritten.
- **Agenten-Vorschläge:** Bei Meilensteinen schlägt der Agent vor, Prüfagenten (plotanalyst, conflictanalyst, canonguardian) einzusetzen.

---

### /roman:plot-check

> Analysiert den aktuellen Plot gegen das gewählte Dramaturgiemodell.

- **Agent:** Plotanalyst
- **Parameter:** keine
- **Ablauf:** Agent liest [[Roman_Split/plot/plot-hauptplot]] + [[Roman_Split/plot/PLOT_WORKING]] + Referenzdokument des gewählten Modells.
- **Prüfkategorien:**
  - Beat-Abgleich: Welche Beats fehlen, sind zu schwach oder falsch platziert?
  - Timing/Proportionen: Stimmen die Akt-Verhältnisse?
  - Kohärenz: Hängende Fäden, unaufgelöste Setups?
  - Bewusste Abweichungen: Konsequenzen dokumentierter Abweichungen?
- **Output:** Prüfbericht im Chat mit Schweregrad-Markierungen (❌ Kritisch, ⚠️ Wichtig, 💡 Hinweis)
- **Nach Szenenausarbeitung:** Kann auch prüfen, ob eine fertige Szene ihren vorgesehenen Beat erfüllt.

---

### /roman:canon-check [scope]

> Führt einen Kanon-Konsistenzcheck für alle in dieser Session geänderten Dokumente durch. Idealerweise vor Session-Ende oder Kontextwechsel aufrufen.

- **Agent:** Canonguardian
- **Parameter:** `[scope]` – optional; schränkt die Prüfung auf einen Verzeichnistyp ein (`plot`, `charaktere`, `beziehungen`, `orte`, `gegenstaende`)
- **Ablauf:**
  1. Agent ermittelt geänderte Dateien via `git status --short`
  2. Lädt alle betroffenen Dokumente
  3. Prüft gegen [[Roman_Split/claude.md]] Abschnitt 1b (kanonisierte Fakten), `kanon/objektiv/` und `kanon/subjektiv/`
  4. Kreuzprüfung: Sind die geänderten Dateien untereinander konsistent?
  5. Prüft referenzierte Entitäten auf Existenz
- **Schweregrade:** ❌ Kanon-Verletzung | ⚠️ Kanon-Warnung | 💡 Kanon-Lücke
- **Output:** Strukturierter Prüfbericht im Chat; keine automatischen Korrekturen
- **Trigger:** Manuell via `/roman:canon-check`; wird von Plotarchitect und Charakterentwickler aktiv vorgeschlagen bei Session-Ende- oder Kontextwechsel-Signalen

---

## Hinweise

- **Autocomplete in Claude Code:** `/roman` im Chat tippen → alle Unterbefehle erscheinen mit Beschreibung.
- **Freie Ansprache:** Der `/roman:plot`-Befehl kann auch durch natürliche Formulierungen aktiviert werden (z.B. „Lass uns am Plot arbeiten").
- **Neue Befehle:** Werden hier ergänzt, sobald sie definiert sind – unabhängig davon, welcher Agent sie ausführt. Gleichzeitig neue Datei unter `.claude/commands/roman/{name}.md` anlegen.
- **Neue Agenten:** Sobald weitere Agenten Slash-Befehle erhalten, wird die Spalte „Agent" in der Übersichtstabelle entsprechend aktualisiert.
