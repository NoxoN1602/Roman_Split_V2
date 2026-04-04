# Befehlsreferenz – Roman-Autorensystem

> **Zweck:** Vollständige Liste aller verfügbaren Slash-Befehle.
> **Letzte Aktualisierung:** 2026-04-04
> **Hinweis:** Diese Datei wird bei jedem neuen Befehl aktualisiert. Claude liest sie zu Beginn jeder Session.

---

## Übersicht

| Nr. | Befehl | Agent | Typ | Kurzbeschreibung |
| --- | ------ | ----- | --- | ---------------- |
| 1 | `/neuer-charakter` | Charakterentwickler | Erstellen | Neuen Charakter anlegen (3-Phasen-Workflow) |
| 2 | `/charakter-erweitern [Name]` | Charakterentwickler | Vertiefen | Bestehenden Charakter abschnittsweise vertiefen |
| 3 | `/ort [Name] [Charakter?]` | Charakterentwickler | Erstellen | Neues Ortsdokument anlegen |
| 4 | `/ort-erweitern [Name]` | Charakterentwickler | Vertiefen | Bestehenden Ort abschnittsweise vertiefen |
| 5 | `/gegenstand [Name] [Charakter?]` | Charakterentwickler | Erstellen | Neues Gegenstandsdokument anlegen |
| 6 | `/gegenstand-erweitern [Name]` | Charakterentwickler | Vertiefen | Bestehenden Gegenstand abschnittsweise vertiefen |
| 7 | `/beziehung [A] [B]` | Charakterentwickler | Erstellen | Neue Beziehung zwischen zwei Entitäten anlegen |
| 8 | `/beziehung-aktualisieren [A] [B]` | Charakterentwickler | Aktualisieren | Bestehende Beziehung manuell aktualisieren |
| 9 | `/check [Name]` | Charakterentwickler | Prüfen | Vollständigkeit und Konsistenz prüfen (alle Typen) |
| 10 | `/szene-auswerten [SZ-ID]` | Charakterentwickler | Pipeline | Veränderungen aus Szene extrahieren und eintragen |

---

## Befehle im Detail

### /neuer-charakter

> Erstellt einen neuen Charakter in drei Phasen.

- **Agent:** Charakterentwickler
- **Parameter:** keine
- **Workflow:**
  1. **Phase 1 – Freies Erzählen:** Der Agent lässt den Autor frei erzählen, stellt danach 3–5 gezielte Nachfragen.
  2. **Phase 2 – Erster Entwurf:** Mapping auf `TEMPLATE-charakter.md`, Datei unter `charaktere/{vorname-nachname}.md`. Zusammenfassung in: Eingetragen / Abgeleitet / Noch offen.
  3. **Phase 3 – Vertiefung (optional):** Kann sofort oder später via `/charakter-erweitern` erfolgen.
- **Output:** Charakter-Datei (Status: ENTWURF)

---

### /charakter-erweitern [Name]

> Vertieft einen bestehenden Charakter Abschnitt für Abschnitt.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Charakters (z.B. `Laura Ahler`)
- **Ablauf:** Agent öffnet Datei → zeigt offene MUSS-Abschnitte → Autor wählt Abschnitt → gezielte Fragen & Vorschläge → Eintragen → nächster Abschnitt. Nach MUSS optional KANN.
- **Output:** Aktualisierte Charakter-Datei

---

### /ort [Name] [Charakter?]

> Erstellt ein neues Ortsdokument in drei Phasen.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Orts, `[Charakter]` – optional, verknüpfter Charakter
- **Workflow:** Identisch zum Charakter-Workflow (3 Phasen), aber mit ortsspezifischen Fragen (Raumgefühl, Sensorik, Atmosphäre, Funktion im Roman).
- **Template:** `TEMPLATE-ort.md`
- **Output:** Ort-Datei unter `orte/{ort-name}.md` (Status: ENTWURF)

---

### /ort-erweitern [Name]

> Vertieft einen bestehenden Ort abschnittsweise.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Orts
- **Ablauf:** Wie `/charakter-erweitern`, aber mit ortsspezifischen Fragen (Licht, Zustand, Sensorische Signatur, Atmosphäre).
- **Output:** Aktualisierte Ort-Datei

---

### /gegenstand [Name] [Charakter?]

> Erstellt ein neues Gegenstandsdokument in drei Phasen.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Gegenstands, `[Charakter]` – optional, verknüpfter Charakter
- **Workflow:** Identisch zum Charakter-Workflow (3 Phasen), aber mit gegenstandsspezifischen Fragen (Material, Herkunft, Besitz, Symbolik).
- **Template:** `TEMPLATE-gegenstand.md`
- **Output:** Gegenstands-Datei unter `gegenstaende/{gegenstand-name}.md` (Status: ENTWURF)

---

### /gegenstand-erweitern [Name]

> Vertieft einen bestehenden Gegenstand abschnittsweise.

- **Agent:** Charakterentwickler
- **Parameter:** `[Name]` – Name des Gegenstands
- **Ablauf:** Wie `/charakter-erweitern`, aber mit gegenstandsspezifischen Fragen (Physische Beschreibung, Herkunft, Symbolik, Grenzen).
- **Output:** Aktualisierte Gegenstands-Datei

---

### /beziehung [A] [B]

> Legt eine neue Beziehung zwischen zwei Entitäten an.

- **Agent:** Charakterentwickler
- **Parameter:** `[A]` und `[B]` – Namen der beteiligten Entitäten (Charaktere, Orte oder Gegenstände)
- **Workflow:** 3-Phasen-Workflow mit beziehungsspezifischen Fragen (Art der Beziehung, Dynamik, subjektive Sichten beider Seiten, Konfliktpotenzial).
- **Template:** `TEMPLATE-beziehung.md`
- **Output:** Beziehungs-Datei unter `beziehungen/{a}--{b}.md` (Status: ENTWURF)

---

### /beziehung-aktualisieren [A] [B]

> Aktualisiert eine bestehende Beziehung manuell.

- **Agent:** Charakterentwickler
- **Parameter:** `[A]` und `[B]` – Namen der beteiligten Entitäten
- **Ablauf:** Agent öffnet BEZ-Datei → zeigt aktuellen Status (letzter Zeitleisten-Eintrag, subjektive Sichten) → fragt nach Veränderung und Auslöser (Szene oder Entwicklung zwischen Szenen) → neuer Zeitleisten-Eintrag.
- **Output:** Aktualisierte Beziehungs-Datei

---

### /check [Name]

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

### /szene-auswerten [SZ-ID]

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

## Hinweise

- **Kein Autocomplete:** In Claude.ai gibt es kein natives Slash-Command-System. Die Befehle werden als normaler Text eingegeben. Bei Unsicherheit einfach fragen: *„Welche Befehle gibt es?"*
- **Neue Befehle:** Werden hier ergänzt, sobald sie definiert sind – unabhängig davon, welcher Agent sie ausführt.
- **Neue Agenten:** Sobald weitere Agenten Slash-Befehle erhalten, wird die Spalte „Agent" in der Übersichtstabelle entsprechend aktualisiert.
