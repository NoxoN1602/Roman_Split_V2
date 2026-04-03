---
typ: konzept
id: KON-0001
titel: "Systemkonzept Roman-Autorensystem"
version: "1.1"
versionen:
  - version: "1.0"
    datum: 2026-04-03
    aenderungen: "Initiales Systemkonzept"
  - version: "1.1"
    datum: 2026-04-03
    aenderungen: "Konzept- und Entscheidungsdokumentation ergaenzt"
betrifft: "Gesamtsystem"
abhaengigkeiten: []
status: aktiv
ersetzt_durch: null
tags:
  - architektur
  - meta
---

# KON-0001 – Systemkonzept Roman-Autorensystem

## 1. Vision

Ein agentengestuetztes Autorensystem auf Basis von Markdown-Dateien in Obsidian, das eine komplette fiktive Welt modelliert. Der Roman entsteht nicht-linear durch Dialog zwischen Autor und spezialisierten Agenten. Ein Kanon-System sichert die innere Konsistenz, waehrend der Autor der Inspiration folgt.

**Grundprinzip:** Der Leser sieht nur die Szenen in der finalen Reihenfolge. Dahinter existiert ein vollstaendiges Weltnetz aus Charakteren, Beziehungen, Orten, Gegenstaenden, Zeitlinien und kanonischen Wahrheiten.

## 2. Verzeichnisstruktur

```
/Roman_Split/
│
├── _system/                          # Systemdateien (nicht Teil des Romans)
│   ├── agenten/                      # Agenten-Definitionen & Prompts
│   ├── templates/                    # Vorlagen fuer alle Dateitypen
│   ├── regeln/                       # Meta-Regeln des Systems
│   ├── konzept/                      # Systemkonzepte & Architektur
│   ├── entscheidungen/               # Architektur-Entscheidungen (ADRs)
│   └── changelog.md                  # Aenderungsprotokoll
│
├── plot/                             # Plot-Architektur
├── charaktere/                       # Ein File pro Charakter
├── beziehungen/                      # Beziehungsdokumente
├── orte/                             # Ortsdokumente
├── gegenstaende/                     # Relevante Gegenstaende
├── kanon/                            # Kanonische Wahrheiten
│   ├── objektiv/                     # Objektive Weltwahrheiten
│   └── subjektiv/                    # Charakter-spezifische Wahrheiten
├── szenen/                           # Die eigentlichen Roman-Szenen
└── reihenfolge/                      # Szenenreihenfolge & Kapitelstruktur
```

### Namenskonventionen
- **Dateinamen:** Kleinbuchstaben, Bindestrich als Worttrenner, keine Umlaute (ae/oe/ue/ss)
- **Romanzeit-Prefix:** `RT` gefolgt von Zeitformat (z.B. `RT0001-03-15` = Jahr 1, Monat 3, Tag 15)
- **Szenen-ID:** `SZ-{vierstellige-nummer}` – fortlaufend nach Erstellungsreihenfolge, NICHT nach Lesereihenfolge
- **Beziehungen:** Alphabetisch sortiert, Doppel-Bindestrich: `anna--berthold.md`

## 3. Frontmatter-Standards

### 3.1 Szene

```yaml
---
typ: szene
id: SZ-0001
titel: "Titel der Szene"
romanzeit_start: "RT0003-07-22T14:00"
romanzeit_ende: "RT0003-07-22T18:30"
orte:
  - "[[ort-name]]"
charaktere:
  - "[[charakter-name]]"
gegenstaende:
  - "[[gegenstand-name]]"
plot_straenge:
  - "[[hauptplot]]"
kanon_referenzen:
  - "[[kanon-eintrag]]"
status: entwurf  # entwurf | review | kanon-geprueft | final
erstellt: 2026-04-03
bearbeitet: 2026-04-03
erstellt_von: ghostwriter
geprueft_von: null
stimmung: ""
konflikt: ""
wendepunkt: false
tags: []
---
```

### 3.2 Charakter

```yaml
---
typ: charakter
name: "Vollstaendiger Name"
id: CHAR-vorname-nachname
alter_bei_start: 0
geschlecht: ""
beruf: ""
zugehoerigkeit: ""
erscheinung: ""
mbti: null
enneagramm: null
kernmotivation: ""
groesste_angst: ""
archetypus: ""
charakter_bogen: ""
beziehungen: []
besitztuemer: []
szenen: []
status: aktiv  # aktiv | verstorben | inaktiv
erstellt: 2026-04-03
tags: []
---
```

### 3.3 Ort

```yaml
---
typ: ort
name: "Name des Orts"
id: ORT-ort-name
region: ""
uebergeordnet: null
untergeordnet: []
visuell: ""
akustisch: ""
geruch: ""
symbolik: ""
atmosphaere: ""
charaktere_verbunden: []
gegenstaende_hier: []
erstellt: 2026-04-03
tags: []
---
```

### 3.4 Gegenstand

```yaml
---
typ: gegenstand
name: "Name des Gegenstands"
id: GGS-gegenstand-name
aussehen: ""
herkunft: ""
symbolik: ""
macguffin: false
besitz_verlauf: []
erstellt: 2026-04-03
tags: []
---
```

### 3.5 Beziehung

```yaml
---
typ: beziehung
id: BEZ-person-a--person-b
person_a: "[[person-a]]"
person_b: "[[person-b]]"
phasen: []
beziehungstyp: ""
machtbalance: ""
erstellt: 2026-04-03
tags: []
---
```

### 3.6 Kanon (objektiv)

```yaml
---
typ: kanon
subtyp: objektiv
id: KAN-OBJ-RT0000-00-00-thema
romanzeit: "RT0000-00-00"
gueltig_ab: "RT0000-00-00"
gueltig_bis: null
thema: ""
verbindlichkeit: absolut  # absolut | stark | weich
betrifft: []
erstellt: 2026-04-03
erstellt_von: kanon-waechter
tags: []
---
```

### 3.7 Kanon (subjektiv)

```yaml
---
typ: kanon
subtyp: subjektiv
id: KAN-SUB-charakter-RT0000-00-00-thema
charakter: "[[charakter-name]]"
romanzeit: "RT0000-00-00"
gueltig_ab: "RT0000-00-00"
gueltig_bis: null
thema: ""
wahrheit_fuer_charakter: true
objektiv_korrekt: true
erstellt: 2026-04-03
erstellt_von: kanon-waechter
tags: []
---
```

### 3.8 Plot-Strang

```yaml
---
typ: plot-strang
name: "Name des Strangs"
id: PLOT-strang-name
struktur_modell: "drei-akt"
schluesselmomente: []
hauptcharaktere: []
zentrale_frage: ""
themen: []
status: in-arbeit
erstellt: 2026-04-03
tags: []
---
```

## 4. Das Kanon-System

### 4.1 Grundregeln

1. **Kanon ist bindend.** Kein Agent darf kanonische Fakten ignorieren.
2. **Zeitgestempelt.** Jeder Kanon-Eintrag hat `gueltig_ab` und optional `gueltig_bis` in Romanzeit.
3. **Objektiv vs. Subjektiv.** Objektiv = Welt wie sie IST. Subjektiv = was ein Charakter GLAUBT (kann falsch sein).
4. **Ueberschreibung.** Neuerer Kanon-Eintrag mit gleichem Thema ueberschreibt aeltere (im Gueltigkeitszeitraum).
5. **Automatische Erzeugung.** Nach jeder Szene erzeugt der Kanon-Waechter neue Kanon-Eintraege.
6. **Konflikterkennung.** Vor dem Schreiben prueft der Kontinuitaets-Pruefer alle relevanten Kanon-Eintraege.

### 4.2 Kanon-Abfrage-Logik

Fuer eine Szene mit `romanzeit_start: RTxxxx`:
1. Alle objektiven Kanon-Eintraege laden mit `gueltig_ab <= RTxxxx` UND (`gueltig_bis > RTxxxx` ODER `gueltig_bis = null`)
2. Fuer jeden beteiligten Charakter: subjektive Kanon-Eintraege mit gleicher Zeitlogik
3. Ortskanon laden
4. Gegenstandskanon laden

### 4.3 Kanon-Kaskade

```
Absoluter Kanon (verbindlichkeit: absolut)
    ↓ ueberstimmt
Starker Kanon (verbindlichkeit: stark)
    ↓ ueberstimmt
Weicher Kanon (verbindlichkeit: weich)
```

- **Absolut:** Unveraenderlich – Naturgesetze, Magie-Regeln, historische Fixen
- **Stark:** Aenderung nur mit expliziter Begruendung und Genehmigung
- **Weich:** Wahrscheinlich so, aber bei Bedarf anpassbar

## 5. Das Agenten-System

### 5.1 Agenten-Uebersicht

| Agent | Rolle | Output |
|---|---|---|
| Plot-Architekt | Co-Autor fuer Handlungsstruktur | `plot/` Dateien |
| Charakter-Entwickler | Tiefenpsychologische Charakterarbeit | `charaktere/` Dateien |
| Beziehungs-Manager | Beziehungsdynamiken | `beziehungen/` Dateien |
| Ghostwriter | Schreibt Szenen | `szenen/` Dateien |
| Kanon-Waechter | Extrahiert Fakten aus Szenen | `kanon/` Dateien |
| Kontinuitaets-Pruefer | Validiert gegen Kanon | Pruefberichte |

### 5.2 Agenten-Aufruf

Im Chat einfach den Agenten benennen:
- "Plot-Architekt, ich will ueber den zweiten Akt reden"
- "Charakter-Entwickler: Ich brauche einen neuen Antagonisten"
- "Ghostwriter: Schreib mir die Szene am Leuchtturm"
- "Kanon-Waechter: Pruef die letzte Szene"

## 6. Workflow: Szene erstellen (nicht-linear)

```
1. Autor gibt Impuls (Ort, Zeit, Charaktere, Ziel)
2. System ordnet zeitlich ein (Romanzeit bestimmen)
3. Kanon-Paket schnueren (relevante Eintraege laden)
4. Ghostwriter schreibt (unter Beachtung aller Vorgaben)
5. Autor reviewt (Feedback, Korrekturen)
6. Kanon-Waechter extrahiert (neue Fakten → Kanon-Eintraege)
7. Kontinuitaets-Pruefer validiert (Pruefbericht)
8. Finalisierung (Status: entwurf → kanon-geprueft → final)
```

## 7. Nicht-lineare Entwicklung: Regeln

1. Szenen-ID ≠ Lesereihenfolge
2. `reihenfolge/lesereihenfolge.md` ist die einzige Quelle der Wahrheit fuer finale Anordnung
3. Rueckwirkender Kanon: Bei Szenen die zeitlich VOR bestehenden spielen → Kompatibilitaetspruefung
4. Kanon-Luecken sind OK
5. Retcon: Wenn neuer Kanon bestehende Szenen ungueltig macht → Retcon-Eintrag + betroffene Szenen markiert als `status: revision-noetig`

## 8. Konzept- und Entscheidungsdokumentation

### Konzeptdokumente (`_system/konzept/`)

| ID-Bereich | Typ |
|---|---|
| KON-0001–0099 | Systemarchitektur |
| KON-0100–0199 | Agenten-Design |
| KON-0200–0299 | Kanon-System |
| KON-0300–0399 | Workflow-Design |
| KON-0400–0499 | Romanspezifisch |
| KON-0500+ | Erweiterungen |

### Architektur-Entscheidungen (`_system/entscheidungen/`)

ADR-Format: Kontext → Entscheidung → Konsequenzen → Verworfene Alternativen

### Zusammenspiel

```
Konzept (KON)          → beschreibt das DESIGN
Entscheidung (ADR)     → begruendet eine EINZELNE WAHL
Changelog              → protokolliert ALLE AENDERUNGEN chronologisch
Regeln                 → definiert BINDENDE NORMEN fuer Agenten
```
