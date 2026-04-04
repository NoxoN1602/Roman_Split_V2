---
typ: entscheidung
id: ADR-0007
titel: "Einheitliche Bekannte Ereignisse in allen Templates"
datum: 2026-04-04
status: akzeptiert
betrifft:
  - "[[TEMPLATE-charakter]]"
  - "[[TEMPLATE-beziehung]]"
  - "[[TEMPLATE-ort]]"
  - "[[TEMPLATE-gegenstand]]"
  - "[[charakterentwickler]]"
tags:
  - architektur
  - template
---

# ADR-0007 – Einheitliche Bekannte Ereignisse in allen Templates

## Kontext

Ort- und Gegenstand-Templates hatten von Anfang an einen Abschnitt „Bekannte Ereignisse" – eine einfache chronologische Tabelle aller Szenen, in denen die Entität vorkommt, mit Kurzbeschreibung und Auswirkung. Charakter- und Beziehungs-Templates hatten diesen Abschnitt nicht, weil dort andere Strukturen existieren, die eine ähnliche Funktion erfüllen:

- **Charakter:** Entwicklungsbogen (Abschnitt 8) mit Wendepunkten und Zeitlichen Zustandsänderungen
- **Beziehung:** Wendepunkte & Bruchstellen (Abschnitt 7) mit eingetretenen und potenziellen Wendepunkten

Die Frage war, ob diese bestehenden Strukturen ausreichen oder ob ein einheitlicher Ereignis-Abschnitt über alle Templates hinweg nötig ist.

## Entscheidung

Alle vier Entitäts-Templates erhalten einen einheitlichen KANN-Abschnitt „Bekannte Ereignisse" mit derselben Tabellenstruktur:

| Szene | Kurzbeschreibung | Auswirkung auf [Entität] |
| ----- | ---------------- | ------------------------ |

**Begründung:**
1. **Unterschiedlicher Zweck:** „Bekannte Ereignisse" ist ein vollständiges Szenen-Log – jede Szene, in der die Entität vorkommt. Der Entwicklungsbogen (Charakter) und die Wendepunkte (Beziehung) dokumentieren nur die bedeutsamen Veränderungen. Ein Charakter kann in 20 Szenen vorkommen, aber nur 3 Wendepunkte haben.
2. **Konsistenz:** `/szene-auswerten` kann nach der Auswertung alle betroffenen Dokumente einheitlich behandeln – jede Entität, die in einer Szene vorkommt, bekommt einen Eintrag in „Bekannte Ereignisse".
3. **Auffindbarkeit:** „In welchen Szenen kommt Lauras Zimmer vor?" ist eine andere Frage als „Wann hat sich Lauras Zimmer verändert?" – erstere beantwortet „Bekannte Ereignisse", letztere die szenenreferenzierten Veränderungen.
4. **`/check` kann Lücken finden:** Wenn eine Szene an einem Ort spielt, der Ort aber keinen Eintrag in „Bekannte Ereignisse" hat, ist das ein Hinweis auf einen fehlenden Auswertungsschritt.

**Nummerierung nach Einfügung:**
- Charakter: Abschnitt 11 (neu), Verknüpfungen verschoben auf 16
- Beziehung: Abschnitt 8 (neu), Verknüpfungen verschoben auf 10
- Ort und Gegenstand: Unverändert (hatten den Abschnitt bereits)

## Konsequenzen

- `/szene-auswerten` hat eine neue Extraktionskategorie „Bekannte Ereignisse", die alle betroffenen Dokumente einheitlich befüllt
- Bestehende Charakter-Dateien (Laura, Marie) und die BEZ-Datei (Laura↔Marie) müssen bei der nächsten Bearbeitung auf die neue Nummerierung angepasst werden
- Leichter Mehraufwand bei der Szenen-Auswertung, da nun auch nicht-verändernde Szenen-Auftritte dokumentiert werden
- Der KANN-Status bedeutet: Der Abschnitt ist empfohlen, aber nicht zwingend. Bei Nebencharakteren, die nur einmal kurz auftreten, kann er leer bleiben.

## Alternativen (verworfen)

- **Kein Ereignis-Abschnitt für Charakter und Beziehung:** Inkonsistent mit Ort und Gegenstand; die Frage „In welchen Szenen kommt Laura vor?" wäre nur über Dataview-Queries oder das Szenen-Verzeichnis beantwortbar, nicht direkt im Charakter-Dokument.
- **Entwicklungsbogen und Wendepunkte erweitern, um auch nicht-verändernde Szenen zu erfassen:** Vermischt zwei verschiedene Zwecke (Veränderungstracking vs. Szenen-Log); macht die bestehenden Abschnitte unübersichtlich.
- **Nur in der Verknüpfungstabelle (Szenen) erfassen:** Die Verknüpfungstabelle hat nur „Funktion" als Spalte, nicht „Kurzbeschreibung" und „Auswirkung" – zu wenig Information für ein nützliches Szenen-Log.
