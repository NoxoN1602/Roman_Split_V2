---
typ: entscheidung
id: ADR-0012
titel: "Valenz-Verlauf in BEZ-Dateien"
datum: 2026-05-03
status: akzeptiert
betrifft:
  - "[[Roman_Split/_system/agenten/charakterentwickler]]"
  - "[[Roman_Split/_system/agenten/canonguardian]]"
  - "[[Roman_Split/_system/templates/TEMPLATE-beziehung]]"
tags:
  - architektur
  - beziehung
  - valenz
---

# ADR-0012 – Valenz-Verlauf in BEZ-Dateien

## Kontext

BEZ-Dateien dokumentieren den Zustand einer Beziehung zwischen zwei Entitäten. Bisher fehlte ein standardisierter Mechanismus, um zu verfolgen, wie sich die emotionale Qualität einer Beziehung über den Handlungsverlauf hinweg verändert. Eine einmalige Zustandsbeschreibung reicht nicht aus, um Entwicklungsbögen abzubilden – insbesondere bei Beziehungen, die zentral für den Thriller-Kern sind (z.B. Valerie ↔ Johannes).

Die Frage war: Wie dokumentieren wir, dass eine Beziehung von neutral zu angespannt zu komplex wechselt, ohne gegen ADR-0004 (keine Redundanz) zu verstoßen?

## Entscheidung

### 1. `valenz_verlauf` als append-only YAML-Liste im Frontmatter

Jede BEZ-Datei führt ein Feld `valenz_verlauf` im Frontmatter. Es ist eine Liste von Einträgen, die **nur erweitert, nie überschrieben** werden.

Jeder Eintrag hat genau drei Felder:

```yaml
valenz_verlauf:
  - ab: "Handlungspunkt oder Beat (z.B. 'Beat 3', 'Querfall-Episode')"
    wert: positiv        # Erlaubte Werte: positiv | negativ | neutral | angespannt | komplex
    grund: "Kurze Begründung (ein Satz)"
```

### 2. Erlaubte Valenz-Werte

| Wert | Bedeutung |
|------|-----------|
| `positiv` | Vertrauen, Zuneigung, Zusammenarbeit |
| `negativ` | Feindseligkeit, Ablehnung, Misstrauen |
| `neutral` | Unbekannte oder gleichgültige Beziehung |
| `angespannt` | Latenter Konflikt, Reibung ohne offene Feindschaft |
| `komplex` | Widersprüchliche Gefühle, ambivalente Dynamik |

### 3. `ab`-Feld referenziert Handlungspunkte, keine Autorendaten

Das `ab`-Feld enthält **immer einen Handlungspunkt** (Beat, Szenentitel, Episodenname), nie ein Autorendatum (kein `2026-05-03`). Grund: Handlungspunkte bleiben stabil, Autorendaten veralten und vermischen Schreibzeit mit Erzählzeit.

### 4. Initialwert bei Anlage der BEZ-Datei

Jede neu angelegte BEZ-Datei erhält beim Anlegen sofort einen ersten `valenz_verlauf`-Eintrag, der den Zustand bei der Erstbegegnung beschreibt. Leere `valenz_verlauf`-Listen sind nicht erlaubt.

### 5. Beziehungen-Index zeigt Progressionskette

Der Beziehungen-Index (`beziehungen/_beziehungen-index.md`) zeigt den aktuellen Valenz-Wert (letzter Eintrag der Liste) und kann optional die Progressionskette aller Werte als Pfeil-Sequenz darstellen.

## Konsequenzen

- **Charakterentwickler v2.1:** Neue Extraktionskategorie in `/szene-auswerten` – bei jeder Szenenauswertung prüfen, ob sich die Valenz einer beteiligten Beziehung verändert hat; ggf. neuen Eintrag vorschlagen. Neuer Parameter für `valenz_verlauf` beim BEZ-Anlegen (Regel 11).
- **Canonguardian v1.1:** Konsistenzprüfung Schritt 5 – bei geänderten BEZ-Dateien prüfen, ob `valenz_verlauf` vorhanden, nicht leer, und die Werte aus dem erlaubten Set stammen.
- **TEMPLATE-beziehung:** `valenz_verlauf` als Pflichtfeld mit Beispiel-Eintrag ergänzt.
- **Alle bestehenden BEZ-Dateien:** Bei Einführung des ADR mit Initialwert befüllt (11 Dateien, Stand 05-03).

## Alternativen (verworfen)

- **Valenz-Wert als einzelnes Frontmatter-Feld:** Verliert die Geschichte der Entwicklung; ADR-0004-konform, aber dramaturgisch blind.
- **Verlauf im Fließtext der BEZ-Datei:** Nicht maschinenlesbar; schwer für Index-Queries; keine einheitliche Struktur.
- **Eigene Verlaufsdatei pro Beziehung:** Zu viel Overhead; Informationsfragmentierung; widerspricht dem Prinzip, dass BEZ-Datei = einzige Quelle für Beziehungszustand.
