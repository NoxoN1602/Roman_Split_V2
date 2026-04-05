---
typ: entscheidung
id: ADR-0009
titel: "Plotentwicklung – Agenten, Workflow und Methodik"
datum: 2026-04-04
status: akzeptiert
betrifft:
  - "[[Roman_Split/_system/agenten/plotarchitect]]"
  - "[[Roman_Split/_system/agenten/plotanalyst]]"
  - "[[Roman_Split/_system/agenten/conflictanalyst]]"
  - "[[Roman_Split/_system/agenten/canonguardian]]"
  - "[[Roman_Split/_system/agenten/sceneideationpartner]]"
  - "[[Roman_Split/_system/agenten/themenmotivationagent]]"
tags:
  - architektur
  - agent
  - plot
  - workflow
---

# ADR-0009 – Plotentwicklung – Agenten, Workflow und Methodik

## Kontext

Nach Abschluss des Kanon-Aufbaus (Charaktere, Orte, Gegenstände, Beziehungen über den Charakterentwickler) wird nun der Plot-Entwicklungs-Workflow definiert. Plot-Entwicklung unterscheidet sich fundamental von der Entitätserstellung: Sie ist nicht template-basiert, sondern dialogisch, iterativ und erfordert sowohl kreative als auch analytische Arbeit. Die zentrale Architekturentscheidung ist die Trennung von Kreation und Prüfung.

## Entscheidungen

### E1: Agenten-Namen ohne Bindestriche

Agenten-IDs werden als zusammengeschriebene Kleinbuchstaben ohne Bindestriche vergeben (konsistent mit dem bestehenden `charakterentwickler`). Die bisherigen Agenten-Namen aus der Entwurfsphase (z.B. `60_PLOT_ARCHITECT`, `10_STORY_ANALYST`) werden nicht übernommen.

**Neue Agenten-IDs:**

| Agent | Typ | Rolle |
|-------|-----|-------|
| `plotarchitect` | Kreativ | Dialogischer Partner für Plotentwicklung |
| `plotanalyst` | Prüfung | Strukturelle Analyse gegen gewähltes Modell |
| `conflictanalyst` | Prüfung | Spannungs- und Konfliktanalyse |
| `canonguardian` | Prüfung | Kanon-Konsistenzprüfung |
| `sceneideationpartner` | Kreativ | Auflösung von Plot-Beats in konkrete Szenen + Szenenverträge |
| `themenmotivationagent` | Prüfung | Themen-/Motiv-Konsistenz (vorgesehen, Ausarbeitung später) |

**Bestehend:**

| Agent | Typ | Rolle |
|-------|-----|-------|
| `charakterentwickler` | Kreativ | Alle Entitätstypen (CHAR, ORT, GGS, BEZ) |

### E2: Trennung von Kreativ- und Prüfagenten

Wer erschafft, prüft sich nicht selbst. Kreativagenten (`plotarchitect`, `sceneideationpartner`, `charakterentwickler`) erzeugen Inhalte. Prüfagenten (`plotanalyst`, `conflictanalyst`, `canonguardian`) analysieren und kritisieren diese Inhalte. Ein Agent übernimmt nie beide Rollen für dasselbe Artefakt.

### E3: Fünf-Stufen-Workflow für Plotentwicklung

Der `plotarchitect` führt den Autor durch einen Workflow in fünf Stufen:

1. **Der Kern (Logline & Prämisse):** Geschichte auf 1–3 Sätze verdichten. Zentrale Frage, Protagonist, Hindernis, Einsatz.
2. **Die Methodik:** Basierend auf dem Kern schlägt der Agent ein oder zwei passende Strukturmodelle vor. Der Autor wählt oder lehnt ab. Auch methodenfreies Arbeiten ist möglich.
3. **Die Makrostruktur:** Plot wird in große Blöcke zerlegt – Akte, Wendepunkte, Schlüsselmomente. Dialogisch: Agent macht Vorschläge, Autor korrigiert.
4. **Sequenzen & Subplots:** Feinere Auflösung der Blöcke. Nebenhandlungen, Kreuzungspunkte der Handlungsstränge.
5. **Szenen-Outline:** Fertige Szenenfolge als Basis für Szenenverträge.

Die Stufen sind nicht starr sequentiell – Rücksprünge sind jederzeit möglich.

### E4: Aufruf und Zustandserkennung

- **Hauptbefehl:** `/plot` – startet oder setzt die Plotentwicklung fort.
- **Prüfbefehl:** `/plot-check` – analysiert den aktuellen Plot (löst `plotanalyst` aus).
- **Freie Ansprache:** Auch natürliche Formulierungen wie „Lass uns über den Plot reden" starten den Plotentwicklungs-Modus.
- **Automatische Zustandserkennung:** Der `plotarchitect` liest das `PLOT_WORKING`-Dokument und erkennt, in welcher Stufe die Entwicklung steht.

### E5: Methodik-Ansatz

Der `plotarchitect` kennt die unterstützten Dramaturgiemodelle im Detail (alle Beats, Stufen, Prinzipien). Er muss sich nicht sklavisch an ein Modell halten – Varianten und begründete Abweichungen sind erlaubt. Sobald ein Modell gewählt ist, dient es als Leitplanke, nicht als Korsett.

### E6: Methoden als separate Referenzdokumente

Die Dramaturgiemodelle werden als eigenständige Markdown-Dateien im Verzeichnis `_system/referenz/` abgelegt. Der `plotarchitect` weiß, wo sie liegen, und konsultiert sie bei Bedarf.

**Initiale Modelle:**
- Save the Cat (Blake Snyder) – 15 Beats
- Drei-Akt-Struktur – klassisch
- Heldenreise (Campbell/Vogler) – 12/17 Stufen
- Dan Harmons Story Circle – 8 Schritte

Weitere Modelle können jederzeit ergänzt werden.

### E7: Zwei Plot-Dokumente

- **Plot-Dokument** (`plot/plot-hauptplot.md` bzw. `plot/plot-{strangname}.md`): Inhaltliches Ergebnis – Logline, gewählte Methode, Akt-Struktur, Beats, Szenenfolge. Bei mehreren Handlungssträngen ein Dokument pro Strang.
- **PLOT_WORKING** (`plot/PLOT_WORKING.md`): Arbeitszustand – aktuelle Stufe, offene Fragen, aufgeschobene Entscheidungen, nächste Schritte. Wird vom `plotarchitect` nach jeder Session aktualisiert.

Die gewählte Methode wird im Plot-Dokument vermerkt, nicht im PLOT_WORKING.

### E8: Agenten-Bewusstsein

Der `plotarchitect` weiß explizit, welche anderen Agenten existieren und was sie können. Er schlägt ihren Einsatz aktiv vor, wenn er ihn für sinnvoll hält oder ein Meilenstein erreicht ist. Er delegiert aber nicht selbst – der Autor entscheidet.

### E9: Szenenverträge über sceneideationpartner

Der `sceneideationpartner` ist zuständig für:
- Auflösung von Plot-Beats in konkrete Szenenideen
- Erstellung der Szenenverträge (POV, Konfliktziel, Ein-/Ausstiegszustand)

Die Grenze zwischen „Szene vorschlagen" und „Szene spezifizieren" ist fließend – ein separater Agent für Szenenverträge würde unnötige Reibung erzeugen.

### E10: Prüf-Workflows bei Meilensteinen

**Vor der Szenenausarbeitung:**
- Der `canonguardian` prüft den Szenenvertrag gegen den bestehenden Kanon, bevor der Ghostwriter loslegt.

**Nach der Szenenausarbeitung:**
- `canonguardian`: immer (Kanon-Konsistenz)
- `plotanalyst`: immer (erfüllt die Szene den vorgesehenen Beat?)
- `conflictanalyst`: optional (Spannungsdynamik)

**Bei Plot-Meilensteinen:**
- Der `plotarchitect` schlägt dem Autor vor, welche Prüfagenten den aktuellen Stand begutachten sollten. Steuerung ist primär manuell, aber der Vorschlag wird aktiv gemacht.

### E11: Themenmotivationagent (vorgesehen)

Ein Agent für die Themen- und Motivebene wird vorgesehen. Er achtet darauf, dass zentrale Themen des Romans konsistent durch den Plot getragen werden. Ausarbeitung erfolgt, wenn der Bedarf klarer ist.

### E12: Kein Orchestrator

Der in der Entwurfsphase vorgesehene `00_ORCHESTRATOR` entfällt. Stattdessen gibt es definierte Pipelines (z.B. `szenen-pipeline.md`) und den Autor als Steuerer. Der `plotarchitect` übernimmt eine beratende Rolle bei der Reihenfolge von Agenten-Einsätzen im Plot-Kontext.

## Konsequenzen

- Sechs neue Agenten-Definitionen müssen erstellt werden (plotarchitect, plotanalyst, conflictanalyst, canonguardian, sceneideationpartner; themenmotivationagent nur vorgesehen)
- Vier Methoden-Referenzdokumente müssen erstellt werden
- Neue Templates für Plot-Dokument und PLOT_WORKING müssen erstellt werden
- Das Verzeichnis `_system/referenz/` muss angelegt werden
- Die `commands.md` muss um `/plot` und `/plot-check` erweitert werden
- Die `claude.md` muss aktualisiert werden
- Die bestehende `szenen-pipeline.md` muss um die Plot-bezogenen Prüfschritte erweitert werden

## Alternativen (verworfen)

- **Alle Plot-Funktionen in einem einzigen Agenten:** Widerspruch zum Prinzip der Trennung von Kreation und Prüfung. Ein Agent, der sich selbst prüft, ist weniger effektiv.
- **Automatische Pipeline ohne manuelle Steuerung:** Zu starr. Der Autor muss entscheiden können, wann welche Prüfung stattfindet. Aktive Vorschläge ja, Automatismus nein.
- **Dramaturgiemodelle als Teil des Agenten-Prompts:** Zu groß, nicht wartbar. Separate Referenzdokumente sind flexibler und können unabhängig aktualisiert werden.
- **Bindestriche in Agenten-IDs (z.B. plot-architect):** Inkonsistent mit bestehendem `charakterentwickler`. Einheitlichkeit hat Vorrang vor Lesbarkeit.
