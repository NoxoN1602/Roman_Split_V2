# Claude Memory – Roman-Autorensystem

> **Zweck:** Permanentes Gedächtnis für alle Entscheidungen rund um das Roman-Autorensystem.
> **Letzte Aktualisierung:** 2026-04-06
> **Hinweis:** Diese Datei wird fortlaufend ergänzt. Claude liest sie zu Beginn jeder Session.

---

## 1. VISION & GRUNDIDEE

Ein agentengestütztes Autorensystem auf Basis von Markdown-Dateien in Obsidian, das eine komplette fiktive Welt modelliert. Der Roman entsteht nicht-linear durch Dialog zwischen Autor (Til) und spezialisierten Agenten. Ein Kanon-System sichert die innere Konsistenz, während der Autor der Inspiration folgt.

**Root-Verzeichnis:** `Roman_Split/` in der Obsidian-Wissensdatenbank (Dropbox-synchronisiert, Git-versioniert).

> ⚠️ **WICHTIG – Datenquellen:** Dokumente auf Google Drive sind für dieses Projekt **NICHT** relevant. Alle projektrelevanten Dateien liegen ausschließlich im Filesystem unter `Roman_Split/`. Claude soll **niemals** in Google Drive suchen.

> ⚠️ **PERMANENTE REGEL – Keine Deltas/Platzhalter:** Niemals Verweise wie „[Abschnitt X unverändert]", „[siehe vorherige Version]" oder ähnliche Platzhalter in Dateien schreiben. `write_file` überschreibt den gesamten Inhalt – Platzhalter führen zu Datenverlust. Immer den vollständigen Text schreiben, auch wenn sich nur ein Abschnitt ändert.

> ⚠️ **PERMANENTE REGEL – bootstrap.md aktuell halten:** Immer wenn eine Datei im Root-Verzeichnis oder in `_system/entscheidungen/`, `_system/agenten/`, `_system/konzept/` oder `_system/regeln/` **neu angelegt oder gelöscht** wird, muss `bootstrap.md` **sofort im selben Arbeitsschritt** angepasst werden – ohne Ausnahme, ohne Rückfrage. Neue Datei → in Pflichtlektüre eintragen. Gelöschte Datei → aus Pflichtlektüre entfernen.

---

## 1b. ROMAN-KURZPROFIL

> **Logline:** Ein traumatisierter Journalist, der den Tod seiner Tochter und seiner Frau nie verwunden hat, beginnt eine Mordserie zu recherchieren, die seine Stadt erschüttert. Was er nicht weiß: Er selbst ist der Mörder. Seine Psyche spaltet die Realität – wo er harmlose Begegnungen erlebt, hinterlässt er Leichen. Als er sich mit der ermittelnden Kommissarin verbündet und verliebt, jagt er sich selbst in eine Wahrheit, die alles zerstören wird.

> **Prämisse:** Kann ein Mensch schuldig sein, wenn er seine Schuld nicht kennt?

> **Genre:** Psychologischer Thriller | **Inspirationen:** Angel Heart, Shutter Island

> **Methode:** Save the Cat (modifiziert) + Story Circle (Subplots) | **Plot-Status:** Stufe 2 ✅ – Stufe 3 steht an

### Kernfiguren

| Figur | Rolle | CHAR-Status |
|-------|-------|-------------|
| Johannes Breier | Protagonist, dissoziativer Serienmörder, Journalist | ✅ v0.5 |
| Valerie de Beer (Val) | KHK Mordkommission, Ermittlerin, romantisches Interesse, entdeckt Wahrheit vor dem Leser | ✅ v0.2 |
| Sündenbock (Name offen) | Hauptverdächtiger, Ablenkungsfigur | ⬜ |
| Redaktions-Vertrauter (Name offen) | Johannes' Anker zur Realität | ⬜ |
| Ermittlungspartner Val (Name offen) | Vals engster Kollege in der Mordkommission | ⬜ |

### Strukturelle Grundentscheidungen

- **Drei Erzählebenen:** Ebene 1 = objektive Gegenwart; Ebene 2 = Johannes' subjektiv entlastete Wahrnehmung (aktuelle Morde + Erinnerungen Tochter/Frau); Ebene 3 = Intermezzi (anonyme Kindheitsfragmente)
- **Konfabulations-Prinzip:** ENTLASTUNG, nicht Romantisierung. Variiert: alltäglich, angenehm, tragisch, romantisch. Spezifisch: Tochter (Rettung statt Ertränken), Frau (Suizid statt Mord), aktuelle Morde (harmlose Begegnungen)
- **Intermezzi:** Erzähltechnik (kein Strang). Anonyme Kindheitsfragmente zwischen Kapiteln. Details → [[Roman_Split/plot/plot-struktur]]
- **Leserführung:** Hinweis-/Gegenhinweis-Waage + Sündenbock
- **Kommissarin-Twist:** Valerie de Beer erkennt Wahrheit über Johannes vor dem Leser; schweigt. Sieht ihn einmal in einem Zustand, der nicht seinem normalen grüblerisch-introvertierten Wesen entspricht (plötzlich offen, charmant, zugewandt). Akkumuliert Hinweise intern, formuliert sie nicht aus. Enthüllung in finaler Szene.
- **Enthüllung Tochter/Frau:** Sehr spät, zusammen mit finaler Mörder-Auflösung
- **Klinisches Profil:** K-PTBS + dissoziative Amnesie + Konfabulation + funktionaler Alkoholismus
- **Trigger:** T1 rote Highheels, T2 Schlüsselklirren, T3 reißender Stoff, T4 weibliches Flüstern; ein einzelner Trigger genügt; variiert zwischen den Taten; 4-Phasen-Ablauf; Alkohol als Verstärker
- **Modus Operandi (kanonisch):** Kontrollierter Jäger im dissoziativen Zustand; außen offen/charmant/präsent (Gegenteil des Normalzustands); opportunistisches Werkzeug (Schlag) + manuelle Strangulation; Abfolge konsistent, Werkzeug variiert; Trigger kann vor oder während der Begegnung zünden. Details → [[Roman_Split/charaktere/johannes-breier]] Abschnitt 6b

### Valerie de Beer – Kurzprofil (kanonisiert)

- **Name:** Valerie de Beer | **Spitzname:** Val
- **Geburtsdatum:** 23. September 1995 | **Alter (Romanzeitpunkt):** ~30
- **Rang:** Kriminalhauptkommissarin (KHK), Mordkommission, seit ca. 2–3 Jahren
- **Herkunft:** Urgrosseltern aus Rotterdam, nach Deutschland emigriert
- **Ausbildung:** Bachelor Polizei, Hochschule für Polizei Villingen-Schwenningen (2013–2016)
- **Karriere:** PK 2016–2019 → KK 2019–2022 → KOK 2022–2023 → KHK 2023/2024
- **Transfer-Trigger:** Kombination A+C ✅ – Querfall mit Todesfolge (bewiesen, aber intern nicht berücksichtigt) → aktive Bewerbung + direktes Gespräch mit Mordkommission-Leiter → Stelle erhalten; erzeugte Ressentiments bei Kollegen
- **Zwillingsschwester:** Mara de Beer, entführt und ermordet ca. 2003 ✅
- **Erscheinung:** 1,73 m, schlank (Kampfsport), androgyn-funktional gekleidet; mittellanges gewelltes dunkelbraunes Haar, direkter abwartender Blick; Referenzbild vorhanden
- **Psychologie:** Emotional gepanzert; Arbeit als Identität und Flucht; Angst vor nachhaltiger Nähe; zerbricht Beziehungen lieber selbst als verletzt zu werden
- **Familiendynamik:** Eltern nach Tod der Schwester innerlich getrennt; Val hielt sie als Kind zusammen; heute sporadischer, distanzierter Kontakt
- **Beziehungsmuster:** 2–3 kurze intensive Beziehungen zu älteren Männern; Faszination durch: Lesbarkeit durch Schicht, Schaden als Vertrautheit, Paradox der Kontrolle ✅
- **Hobby:** Kampfsport, vermutlich Kickboxen ⬜ (noch nicht endgültig kanonisiert)
- **Offen:** Was bricht ihre Rüstung ❓ | Wohnort ❓ | Ermittlungspartner-Name ❓ | Hobbys endgültig ❓

---

## 2. ARCHITEKTUR-ENTSCHEIDUNGEN (Kurzreferenz)

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
| 0010 | Obsidian-Wiki-Links | Alle Projektdokument-Verweise als `[[Roman_Split/pfad/datei]]` |
| 0011 | BEZ-Lebenszyklus | Keine BEZ vor Erstbegegnung; Anlage als Pflichtschritt in `/szene-auswerten`; halbautomatisch |

---

## 3. NAMENSKONVENTIONEN (naming-conventions.md v2.0)

Kleinbuchstaben, Bindestrich, keine Umlaute. Agenten-IDs zusammengeschrieben ohne Bindestriche.

| Verzeichnis | Muster | Beispiel |
|-------------|--------|----------|
| `charaktere/` | `{vorname-nachname}.md` | `johannes-breier.md` |
| `beziehungen/` | `{char1}--{char2}.md` | `laura-ahler--marie-kanter.md` |
| `orte/` | `{ort-name}.md` | `lauras-zimmer.md` |
| `gegenstaende/` | `{name}.md` | `lauras-armband.md` |
| `szenen/` | `SZ-{nnnn}-{kurztitel}.md` | `SZ-0042-erstes-treffen.md` |
| `_system/agenten/` | `{agentenid}.md` | `plotarchitect.md` |
| `_system/referenz/` | `REF-{methode}.md` | `REF-save-the-cat.md` |
| `plot/` | `plot-{name}.md` | `plot-hauptplot.md`, `plot-struktur.md`, `plot-beats.md` |

---

## 4. VERZEICHNISSTRUKTUR

```
/Roman_Split/
├── claude.md / commands.md / bootstrap.md
├── _system/ (agenten/, referenz/, templates/, regeln/, konzept/, entscheidungen/, changelog.md)
├── plot/ (hauptplot, struktur, beats, PLOT_WORKING, _plot-uebersicht)
├── charaktere/ / beziehungen/
├── orte/ (+ grundrisse/) / gegenstaende/ (+ bilder/)
├── kanon/ (objektiv/ + subjektiv/)
├── szenen/ / reihenfolge/
```

---

## 5. AGENTEN-SYSTEM

Trennung Kreation / Prüfung (ADR-0009). Kein Orchestrator – Autor steuert.

| Agent-ID | Typ | Rolle | Status |
|----------|-----|-------|--------|
| `charakterentwickler` | Kreativ | CHAR, ORT, GGS, BEZ | ✅ v2.0 |
| `plotarchitect` | Kreativ | Dialogischer Plot-Entwicklungspartner | ✅ v1.1 |
| `sceneideationpartner` | Kreativ | Szenen-Auflösung + Szenenverträge | ✅ v1.0 |
| `plotanalyst` | Prüfung | Strukturanalyse gegen Modell | ✅ v1.0 |
| `conflictanalyst` | Prüfung | Spannungs-/Konfliktanalyse | ✅ v1.0 |
| `canonguardian` | Prüfung | Kanon-Konsistenzprüfung | ✅ v1.0 |
| `themenmotivationagent` | Prüfung | Themen-/Motiv-Konsistenz | ⬜ Vorgesehen |

---

## 6. PLOT-SYSTEM (ADR-0009)

Stufen: 1 Kern ✅ | 2 Methodik ✅ | **3 Makrostruktur ⬜** | 4 Sequenzen | 5 Szenen-Outline

Modelle: **Save the Cat** (Hauptmodell) + **Story Circle** (Subplots). Slash-Befehle: `/plot`, `/plot-check`.

### Plot-Dokumente (aufgeteilt seit 04-05)

| Dokument | Inhalt | Wann lesen |
|----------|--------|-----------|
| [[Roman_Split/plot/plot-hauptplot]] | Kompakte Übersicht: Kern, Methodik, Figuren, Verweise | Immer zuerst |
| [[Roman_Split/plot/plot-struktur]] | Stabile Entscheidungen: Erzählebenen, Konfabulation, Waage, Intermezzi | Bei strukturellen Fragen |
| [[Roman_Split/plot/plot-beats]] | 15 Beats mit Inhalten (Stufe 3 Arbeitsdokument) | Bei Makrostruktur-Arbeit |
| [[Roman_Split/plot/PLOT_WORKING]] | Arbeitszustand, Session-Protokoll, nächste Schritte | Immer zuerst |
| [[Roman_Split/plot/_plot-uebersicht]] | Index aller Plot-Dokumente | Bei Orientierung |
| [[Roman_Split/plot/plot-subplots]] | Subplots mit Story Circles | Erst in Stufe 4 |
| [[Roman_Split/plot/plot-szenen]] | Szenen-Outline | Erst in Stufe 5 |

---

## 7. KANON-SYSTEM

Siehe [[Roman_Split/_system/regeln/kanon-regeln]]. Johannes' subjektiver Kanon weicht fundamental vom objektiven ab (entlastete Erinnerungen vs. tatsächliche Morde). Dramatic-Irony-Modellierung ist Kernmechanik.

---

## 8. SZENEN-WORKFLOW

Siehe [[Roman_Split/_system/regeln/szenen-pipeline]] und [[Roman_Split/_system/regeln/szenen-lebenszyklus]]. Wird um Plot-Prüfschritte erweitert (ADR-0009 E10).

---

## 9. TEMPLATES

| Template | Version | Status |
|----------|---------|--------|
| Charakter | v1.2 | ✅ Getestet |
| Beziehung | v1.1 | ✅ Getestet |
| Ort | v1.3 | ✅ Getestet |
| Gegenstand | v1.3 | ✅ Getestet |
| Plot-Dokument | v1.0 | ✅ |
| PLOT_WORKING | v1.0 | ✅ |
| Szene / Kanon | – | ⬜ Offen |

---

## 10. BOOTSTRAP-KONZEPT

✅ **Erstellt:** `bootstrap.md` liegt im Root-Verzeichnis (`Roman_Split/bootstrap.md`).

Die Datei definiert die vollständige Pflichtlektüre für jeden Session-Start:
- Root: `claude.md`, `commands.md`
- `_system/entscheidungen/`: alle ADRs (0001–0011)
- `_system/agenten/`: alle Agenten-Prompts
- `_system/konzept/`: KON-0001
- `_system/regeln/`: alle Regeldokumente

Bedingte Zusatzlektüre (Plot, Charaktere, Szenen) wird bedarfsgesteuert geladen.

**Wartungsregel:** Bei jeder Neuanlage oder Löschung einer Datei in Root, entscheidungen, agenten, konzept oder regeln muss `bootstrap.md` sofort im gleichen Schritt aktualisiert werden.

---

## 11. TESTRESULTATE

| Test | Status | Datei(en) |
|------|--------|-----------|
| Laura Ahler | ✅ | [[Roman_Split/charaktere/laura-ahler]] |
| Marie Kanter | ✅ | [[Roman_Split/charaktere/marie-kanter]] |
| Laura↔Marie | ✅ | [[Roman_Split/beziehungen/laura-ahler--marie-kanter]] |
| Lauras Zimmer | ✅ | [[Roman_Split/orte/lauras-zimmer]] |
| Lauras Armband | ✅ | [[Roman_Split/gegenstaende/lauras-armband]] |
| Valerie de Beer | ✅ v0.2 | [[Roman_Split/charaktere/valerie-de-beer]] |

---

## 12. OFFENE PUNKTE

### Plot-Entwicklung
- [x] Stufe 1+2 ✅ | [x] Johannes CHAR v0.5 ✅ | [x] Trigger ✅ | [x] Klinisches Profil ✅ | [x] Konfabulations-Prinzip ✅ | [x] Intermezzi ✅ | [x] Modus Operandi ✅
- [x] **Valerie de Beer CHAR v0.2 ✅** – Transfer-Trigger, Schwester Mara, Kampfsport kanonisiert
- [ ] **Stufe 3 (Makrostruktur)** | [ ] Sündenbock CHAR | [ ] Vertrauter CHAR | [ ] Johannes vertiefen (Details)
- [ ] Valerie vertiefen: Was bricht ihre Rüstung ❓ | Wohnort ❓ | Ermittlungspartner ❓ | Hobbys endgültig ❓

### System-Entwicklung
- [x] Plotarchitect über neue Dokumentenstruktur informieren ✅ (v1.1)
- [x] Bootstrap.md ✅
- [x] BEZ-Lebenszyklus definiert ✅ (ADR-0011)
- [ ] szenen-pipeline erweitern | [ ] Kanon-/Szenen-Templates | [ ] Ghostwriter-Agent

---

## 13. CHRONOLOGIE

| Datum | Was |
|-------|-----|
| 04-03 | Grundidee, Systemkonzept, ADR-0001–0003, CHAR/BEZ-Templates + Tests |
| 04-04 | ORT/GGS-Templates, ADR-0004–0009, Plotentwicklung, commands.md, Stufe 1+2 abgeschlossen |
| 04-05 | CHAR-johannes-breier v0.1→v0.4: Trigger-System, klinisches Profil, Konfabulations-Prinzip |
| 04-05 | Intermezzi als Erzähltechnik. Drei Erzählebenen. Terminologie korrigiert (Entlastung statt Romantisierung). |
| 04-05 | **Plot-Dokumente aufgeteilt:** hauptplot (Übersicht), struktur (stabile Entscheidungen), beats (Stufe 3). Delta-Regel als permanente Regel eingeführt. Plotarchitect v1.0→v1.1. |
| 04-05 | **ADR-0010:** Obsidian-Wiki-Links als Standard für alle internen Verlinkungen eingeführt. Alle Systemdokumente aktualisiert. |
| 04-05 | **bootstrap.md erstellt** im Root-Verzeichnis. Definiert vollständige Pflichtlektüre für Session-Start. |
| 04-05 | **Wartungsregel bootstrap.md** eingeführt. In claude.md und bootstrap.md verankert. |
| 04-05 | **Modus Operandi definiert:** Kontrollierter Jäger im dissoziativen Zustand. Opportunistisches Werkzeug + manuelle Strangulation. Dissoziativer Zustand als Abschnitt 6b in CHAR-johannes-breier. Johannes v0.4→v0.5. |
| 04-05 | **ADR-0011:** BEZ-Lebenszyklus definiert. Keine BEZ vor Erstbegegnung. Pflichtschritt in `/szene-auswerten`, halbautomatisch. Charakterentwickler v1.8→v1.9. |
| 04-06 | **CHAR-valerie-de-beer v0.1 erstellt.** Name, KHK-Rang, Karrierepfad, Psychologie, Beziehungsmuster, Faszination ältere Männer kanonisiert. Referenzbild vorhanden. |
| 04-06 | **CHAR-valerie-de-beer v0.2.** Transfer-Trigger (Kombination A+C) kanonisiert. Zwillingsschwester: Mara de Beer. Kampfsport als Hobby (Kickboxen noch nicht final). |

---

<!-- 
ANWEISUNGEN FÜR CLAUDE:
- Lies diese Datei und commands.md zu Beginn jeder Session.
- **NIEMALS Google Drive durchsuchen** – nur Filesystem unter Roman_Split/.
- **NIEMALS Deltas/Platzhalter in Dateien schreiben** – immer vollständigen Text. write_file überschreibt alles.
- **NIEMALS bootstrap.md veralten lassen:** Neue Datei in Root/entscheidungen/agenten/konzept/regeln → sofort in bootstrap.md eintragen. Gelöschte Datei → sofort entfernen. Kein separater Schritt, immer im selben Arbeitsschritt.
- Bei Architektur-Entscheidungen: IMMER ADR erstellen.
- Bei Widersprüchen: claude.md + ADRs gelten.
- Namenskonventionen: ADR-0003 / [[Roman_Split/_system/regeln/naming-conventions]] v2.1.
- Neue Slash-Befehle: IMMER in [[Roman_Split/commands]] eintragen.
- Roman-Plot: Lies [[Roman_Split/plot/PLOT_WORKING]] + [[Roman_Split/plot/plot-hauptplot]] für den aktuellen Stand. [[Roman_Split/plot/plot-struktur]] bei Bedarf. [[Roman_Split/plot/plot-beats]] für Makrostruktur.
- Dramaturgiemodell: Save the Cat (modifiziert) + Story Circle (Subplots).
- Johannes Breier: CHAR v0.5. Trigger, klinisches Profil, Konfabulations-Prinzip, Modus Operandi kanonisch.
- **Konfabulations-Prinzip:** ENTLASTUNG (Schuld entfernen), NICHT Romantisierung. Variiert: alltäglich, angenehm, tragisch oder romantisch.
- **Modus Operandi:** Kontrollierter Jäger im dissoziativen Zustand. Außenwirkung: offen/charmant/präsent. Opportunistisches Werkzeug + manuelle Strangulation. Trigger variiert zwischen Taten. Details → CHAR Abschnitt 6b.
- **BEZ-Lebenszyklus (ADR-0011):** Keine BEZ vor Erstbegegnung. In /szene-auswerten: Erstbegegnungen erkennen = Pflichtschritt, halbautomatisch (Autor bestätigt).
- **Valerie de Beer (Val):** CHAR v0.2. KHK. Geb. 23.09.1995. Villingen-Schwenningen. Zwillingsschwester Mara (ermordet ~2003). Transfer: Querfall bewiesen + direktes Gespräch mit Mordkommission-Leiter (Ressentiments bei Kollegen). Psychologie: emotional gepanzert, Arbeit als Identität, Angst vor Nähe. Beziehungsmuster: bricht selbst ab. Faszination ältere Männer: Lesbarkeit durch Schicht + Schaden als Vertrautheit + Paradox der Kontrolle. Kampfsport (Kickboxen noch nicht final). Referenzbild vorhanden.
- Session-Initialisierung: Siehe bootstrap.md für vollständige Pflichtlektüre-Liste.
-->
