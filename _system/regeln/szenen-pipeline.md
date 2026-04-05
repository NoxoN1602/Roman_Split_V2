---
typ: regel
id: REG-szenen-pipeline
titel: "Szenen-Pipeline nach Abnahme"
version: "1.0"
status: aktiv
siehe_auch:
  - "[[Roman_Split/_system/regeln/szenen-lebenszyklus]]"
  - "[[Roman_Split/_system/agenten/charakterentwickler]]"
  - "[[Roman_Split/_system/regeln/kanon-regeln]]"
tags:
  - regel
  - pipeline
  - workflow
---

# Szenen-Pipeline nach Abnahme

## Übersicht

Diese Pipeline wird automatisch ausgelöst, wenn eine Szene den Status `abgenommen` erhält – entweder zum ersten Mal oder nach einer Revision. Sie stellt sicher, dass alle Auswirkungen einer Szene in den entsprechenden Dokumenten nachgeführt werden.

**Auslöser:** Szenen-Status wechselt zu `abgenommen`
**Trigger:** Der Ghostwriter fragt nach Abschluss einer Szene: *„Soll die Szene abgenommen werden?"* Bei „Ja" startet die Pipeline. Alternativ manueller Aufruf durch den Autor.

---

## Pipeline-Schritte

Die Schritte werden in dieser Reihenfolge ausgeführt. Jeder Schritt muss abgeschlossen sein, bevor der nächste beginnt.

### Schritt 1: Kontinuitäts-Prüfung

**Zuständig:** Kontinuitäts-Prüfer (AGT-kontinuitaets-pruefer)

**Aufgabe:**
- Szene gegen bestehenden Kanon prüfen
- Zeitliche Konsistenz prüfen (Romanzeit, Reihenfolge)
- Prüfen, ob referenzierte Charaktere, Orte, Gegenstände existieren
- Prüfen, ob Charakterverhalten mit Abschnitt 10 (Grenzen & Verbote) vereinbar ist

**Mögliche Ergebnisse:**
- ✅ Keine Konflikte → Weiter zu Schritt 2
- ⚠️ Warnungen (geringfügig) → Warnungen anzeigen, Autor entscheidet, ob fortgefahren wird
- ❌ Kanon-Verletzung → Pipeline stoppt. Szene geht zurück auf `revision`

---

### Schritt 2: Charakter-Auswertung

**Zuständig:** Charakterentwickler (AGT-charakterentwickler)
**Slash-Befehl:** `/szene-auswerten [SZ-ID]`

**Aufgabe:**
- Alle Charakter-relevanten Veränderungen aus der Szene extrahieren
- Kategorien der Extraktion:
  - **Physische Veränderungen** (Verletzungen, Erscheinungsänderungen) → Abschnitt 2.2 + Abschnitt 8 (Zeitliche Zustandsänderungen)
  - **Psychologische Veränderungen** (Erkenntnisse, Traumata, Wendepunkte) → Abschnitt 8 (Entwicklungsbogen)
  - **Beziehungsveränderungen** (neue Beziehungen, Brüche, Verschiebungen) → Abschnitt 7 + BEZ-Dokumente
  - **Neue Verknüpfungen** (Charakter begegnet neuem Ort/Gegenstand) → Abschnitt 15
  - **Status-Änderungen** (Beruf, Wohnort, Familienstand) → Abschnitt 2

**Ablauf:**
1. Agent liest die Szene vollständig
2. Agent liest die betroffenen Charakter-Dateien
3. Agent erstellt eine Änderungsliste: *„Folgende Änderungen habe ich erkannt:"*
4. Autor bestätigt oder korrigiert
5. Agent trägt bestätigte Änderungen in die Dokumente ein
6. Agent aktualisiert Frontmatter (Version, Datum) in allen geänderten Dateien

---

### Schritt 3: Kanon-Ableitung

**Zuständig:** Kanon-Wächter (AGT-kanon-waechter)

**Aufgabe:**
- Aus den in Schritt 2 bestätigten Änderungen Kanon-Einträge ableiten
- Objektive Kanon-Einträge erstellen (was ist in der Welt passiert?)
- Subjektive Kanon-Einträge erstellen (was weiß/glaubt welcher Charakter jetzt?)
- Romanzeit-Stempel setzen

**Ablauf:**
1. Agent liest die Änderungsliste aus Schritt 2
2. Agent schlägt Kanon-Einträge vor
3. Autor bestätigt
4. Agent erstellt Kanon-Dateien unter `kanon/objektiv/` und/oder `kanon/subjektiv/`

---

## Pipeline bei Revision

Wenn eine zuvor abgenommene Szene erneut abgenommen wird (Status: `revision` → `abgenommen` v2+), gelten zusätzliche Regeln:

1. **Delta-Modus:** Die Pipeline vergleicht die neue Version mit der vorherigen und identifiziert nur die Unterschiede.
2. **Veraltete Markierungen entfernen:** Die `⚠️ potenziell veraltet`-Flags, die beim Öffnen der Revision gesetzt wurden, werden entfernt oder aktualisiert.
3. **Kanon-Einträge aktualisieren:** Bestehende Kanon-Einträge, die auf dieser Szene basieren, werden überprüft und ggf. angepasst (nicht neu erstellt, sondern aktualisiert).

---

## Pipeline-Protokoll

Nach Abschluss der Pipeline wird ein kurzer Eintrag im Changelog erstellt:

```
- **Pipeline:** SZ-{id} v{version} abgenommen.
  - Kontinuitaet: ✅ / ⚠️ / ❌
  - Charakter-Updates: [Liste der geaenderten Dateien]
  - Kanon-Eintraege: [Liste der erstellten/aktualisierten Eintraege]
```

---

## Manuelle Auslösung einzelner Schritte

Jeder Pipeline-Schritt kann auch unabhängig manuell ausgelöst werden:

| Schritt | Manueller Aufruf |
|---|---|
| Kontinuitäts-Prüfung | Kontinuitäts-Prüfer direkt aufrufen |
| Charakter-Auswertung | `/szene-auswerten [SZ-ID]` beim Charakterentwickler |
| Kanon-Ableitung | Kanon-Wächter direkt aufrufen |

Dies ermöglicht auch die Auswertung von Szenen im Status `entwurf` – z.B. um vorab zu prüfen, welche Auswirkungen eine Szene hätte, ohne sie offiziell abzunehmen.
