# Claude Memory – Roman-Autorensystem

> **Zweck:** Permanentes Gedächtnis für alle Entscheidungen rund um das Roman-Autorensystem.
> **Letzte Aktualisierung:** 2026-04-05
> **Hinweis:** Diese Datei wird fortlaufend ergänzt. Claude liest sie zu Beginn jeder Session.

---

## 1. VISION & GRUNDIDEE

Ein agentengestütztes Autorensystem auf Basis von Markdown-Dateien in Obsidian, das eine komplette fiktive Welt modelliert. Der Roman entsteht nicht-linear durch Dialog zwischen Autor (Til) und spezialisierten Agenten. Ein Kanon-System sichert die innere Konsistenz, während der Autor der Inspiration folgt.

**Root-Verzeichnis:** `Roman_Split/` in der Obsidian-Wissensdatenbank (Dropbox-synchronisiert, Git-versioniert).

> ⚠️ **WICHTIG – Datenquellen:** Dokumente auf Google Drive sind für dieses Projekt **NICHT** relevant. Alle projektrelevanten Dateien liegen ausschließlich im Filesystem unter `Roman_Split/`. Claude soll **niemals** in Google Drive suchen.

> ⚠️ **PERMANENTE REGEL – Keine Deltas/Platzhalter:** Niemals Verweise wie „[Abschnitt X unverändert]", „[siehe vorherige Version]" oder ähnliche Platzhalter in Dateien schreiben. `write_file` überschreibt den gesamten Inhalt – Platzhalter führen zu Datenverlust. Immer den vollständigen Text schreiben, auch wenn sich nur ein Abschnitt ändert.

---

## 1b. ROMAN-KURZPROFIL

> **Logline:** Ein traumatisierter Journalist, der den Tod seiner Tochter und seiner Frau nie verwunden hat, beginnt eine Mordserie zu recherchieren, die seine Stadt erschüttert. Was er nicht weiß: Er selbst ist der Mörder. Seine Psyche spaltet die Realität – wo er harmlose Begegnungen erlebt, hinterlässt er Leichen. Als er sich mit der ermittelnden Kommissarin verbündet und verliebt, jagt er sich selbst in eine Wahrheit, die alles zerstören wird.

> **Prämisse:** Kann ein Mensch schuldig sein, wenn er seine Schuld nicht kennt?

> **Genre:** Psychologischer Thriller | **Inspirationen:** Angel Heart, Shutter Island

> **Methode:** Save the Cat (modifiziert) + Story Circle (Subplots) | **Plot-Status:** Stufe 2 ✅ – Stufe 3 steht an

### Kernfiguren

| Figur | Rolle | CHAR-Status |
|-------|-------|-------------|
| Johannes Breier | Protagonist, dissoziativer Serienmörder, Journalist | ✅ v0.4 |
| Kommissarin (Name offen) | Ermittlerin, romantisches Interesse, entdeckt Wahrheit vor dem Leser | ⬜ |
| Sündenbock (Name offen) | Hauptverdächtiger, Ablenkungsfigur | ⬜ |
| Redaktions-Vertrauter (Name offen) | Johannes' Anker zur Realität | ⬜ |

### Strukturelle Grundentscheidungen

- **Drei Erzählebenen:** Ebene 1 = objektive Gegenwart; Ebene 2 = Johannes' subjektiv entlastete Wahrnehmung (aktuelle Morde + Erinnerungen Tochter/Frau); Ebene 3 = Intermezzi (anonyme Kindheitsfragmente)
- **Konfabulations-Prinzip:** ENTLASTUNG, nicht Romantisierung. Variiert: alltäglich, angenehm, tragisch, romantisch. Spezifisch: Tochter (Rettung statt Ertränken), Frau (Suizid statt Mord), aktuelle Morde (harmlose Begegnungen)
- **Intermezzi:** Erzähltechnik (kein Strang). Anonyme Kindheitsfragmente zwischen Kapiteln. Details → `plot-struktur.md`
- **Leserführung:** Hinweis-/Gegenhinweis-Waage + Sündenbock
- **Kommissarin-Twist:** Erkennt Wahrheit vor dem Leser; verrät es nicht
- **Enthüllung Tochter/Frau:** Sehr spät, zusammen mit finaler Mörder-Auflösung
- **Klinisches Profil:** K-PTBS + dissoziative Amnesie + Konfabulation + funktionaler Alkoholismus
- **Trigger:** T1 rote Highheels, T2 Schlüsselklirren, T3 reißender Stoff, T4 weibliches Flüstern; 4-Phasen-Ablauf; Alkohol als Verstärker

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
├── claude.md / commands.md
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
| `charakterentwickler` | Kreativ | CHAR, ORT, GGS, BEZ | ✅ v1.8 |
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
| `plot-hauptplot.md` | Kompakte Übersicht: Kern, Methodik, Figuren, Verweise | Immer zuerst |
| `plot-struktur.md` | Stabile Entscheidungen: Erzählebenen, Konfabulation, Waage, Intermezzi | Bei strukturellen Fragen |
| `plot-beats.md` | 15 Beats mit Inhalten (Stufe 3 Arbeitsdokument) | Bei Makrostruktur-Arbeit |
| `PLOT_WORKING.md` | Arbeitszustand, Session-Protokoll, nächste Schritte | Immer zuerst |
| `_plot-uebersicht.md` | Index aller Plot-Dokumente | Bei Orientierung |
| `plot-subplots.md` | Subplots mit Story Circles | Erst in Stufe 4 |
| `plot-szenen.md` | Szenen-Outline | Erst in Stufe 5 |

---

## 7. KANON-SYSTEM

Siehe `_system/regeln/kanon-regeln.md`. Johannes' subjektiver Kanon weicht fundamental vom objektiven ab (entlastete Erinnerungen vs. tatsächliche Morde). Dramatic-Irony-Modellierung ist Kernmechanik.

---

## 8. SZENEN-WORKFLOW

Siehe `_system/regeln/szenen-pipeline.md` und `szenen-lebenszyklus.md`. Wird um Plot-Prüfschritte erweitert (ADR-0009 E10).

---

## 9. TEMPLATES

| Template | Version | Status |
|----------|---------|--------|
| Charakter | v1.1 | ✅ Getestet |
| Beziehung | v1.1 | ✅ Getestet |
| Ort | v1.3 | ✅ Getestet |
| Gegenstand | v1.3 | ✅ Getestet |
| Plot-Dokument | v1.0 | ✅ |
| PLOT_WORKING | v1.0 | ✅ |
| Szene / Kanon | – | ⬜ Offen |

---

## 10. BOOTSTRAP-KONZEPT

Noch nicht erstellt. `bootstrap.md` geplant.

---

## 11. TESTRESULTATE

| Test | Status | Datei(en) |
|------|--------|-----------|
| Laura Ahler | ✅ | `charaktere/laura-ahler.md` |
| Marie Kanter | ✅ | `charaktere/marie-kanter.md` |
| Laura↔Marie | ✅ | `beziehungen/laura-ahler--marie-kanter.md` |
| Lauras Zimmer | ✅ | `orte/lauras-zimmer.md` |
| Lauras Armband | ✅ | `gegenstaende/lauras-armband.md` |

---

## 12. OFFENE PUNKTE

### Plot-Entwicklung
- [x] Stufe 1+2 ✅ | [x] Johannes CHAR v0.4 ✅ | [x] Trigger ✅ | [x] Klinisches Profil ✅ | [x] Konfabulations-Prinzip ✅ | [x] Intermezzi ✅
- [ ] **Stufe 3 (Makrostruktur)** | [ ] **Tötungsmethode** | [ ] **Kommissarin CHAR** | [ ] Sündenbock CHAR | [ ] Vertrauter | [ ] Johannes vertiefen (Details)

### System-Entwicklung
- [x] Plotarchitect über neue Dokumentenstruktur informieren ✅ (v1.1)
- [ ] szenen-pipeline.md erweitern | [ ] Kanon-/Szenen-Templates | [ ] Bootstrap.md | [ ] Ghostwriter-Agent

---

## 13. CHRONOLOGIE

| Datum | Was |
|-------|-----|
| 04-03 | Grundidee, Systemkonzept, ADR-0001–0003, CHAR/BEZ-Templates + Tests |
| 04-04 | ORT/GGS-Templates, ADR-0004–0009, Plotentwicklung, commands.md, Stufe 1+2 abgeschlossen |
| 04-05 | CHAR-johannes-breier v0.1→v0.4: Trigger-System, klinisches Profil, Konfabulations-Prinzip |
| 04-05 | Intermezzi als Erzähltechnik. Drei Erzählebenen. Terminologie korrigiert (Entlastung statt Romantisierung). |
| 04-05 | **Plot-Dokumente aufgeteilt:** hauptplot (Übersicht), struktur (stabile Entscheidungen), beats (Stufe 3). Delta-Regel als permanente Regel eingeführt. Plotarchitect v1.0→v1.1. |

---

<!-- 
ANWEISUNGEN FÜR CLAUDE:
- Lies diese Datei und commands.md zu Beginn jeder Session.
- **NIEMALS Google Drive durchsuchen** – nur Filesystem unter Roman_Split/.
- **NIEMALS Deltas/Platzhalter in Dateien schreiben** – immer vollständigen Text. write_file überschreibt alles.
- Bei Architektur-Entscheidungen: IMMER ADR erstellen.
- Bei Widersprüchen: claude.md + ADRs gelten.
- Namenskonventionen: ADR-0003 / naming-conventions.md v2.1.
- Neue Slash-Befehle: IMMER in commands.md eintragen.
- Roman-Plot: Lies PLOT_WORKING.md + plot-hauptplot.md für den aktuellen Stand. plot-struktur.md bei Bedarf. plot-beats.md für Makrostruktur.
- Dramaturgiemodell: Save the Cat (modifiziert) + Story Circle (Subplots).
- Johannes Breier: CHAR v0.4. Trigger, klinisches Profil, Konfabulations-Prinzip kanonisch.
- **Konfabulations-Prinzip:** ENTLASTUNG (Schuld entfernen), NICHT Romantisierung. Variiert: alltäglich, angenehm, tragisch oder romantisch.
-->
