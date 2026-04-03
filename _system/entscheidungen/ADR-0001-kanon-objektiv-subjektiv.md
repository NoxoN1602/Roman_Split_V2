---
typ: entscheidung
id: ADR-0001
titel: "Kanon getrennt in objektiv und subjektiv"
datum: 2026-04-03
status: akzeptiert
betrifft:
  - "[[KON-0001-systemkonzept]]"
tags:
  - kanon
  - architektur
---

# ADR-0001 – Kanon getrennt in objektiv und subjektiv

## Kontext

Charaktere in einem Roman wissen nicht alles. Ein Charakter kann etwas glauben, das objektiv falsch ist. Dieses Nichtwissen ist oft ein zentrales Handlungselement (Dramatic Irony). Ein einzelner Kanon-Typ kann diese Unterscheidung nicht abbilden.

## Entscheidung

Wir trennen den Kanon in zwei Kategorien:
- **Objektiv (`kanon/objektiv/`):** Wie die Welt wirklich ist. Gilt als absolute Wahrheit.
- **Subjektiv (`kanon/subjektiv/{charakter}/`):** Was ein Charakter zu einem bestimmten Zeitpunkt glaubt oder weiss. Hat ein Feld `objektiv_korrekt: true|false`.

## Konsequenzen

- Der Ghostwriter muss bei jeder Szene sowohl objektiven als auch subjektiven Kanon des jeweiligen Charakters laden
- Dramatic Irony wird explizit modellierbar
- Hoeherer Pflegeaufwand: Jede neue Information muss doppelt geprueft werden (was passiert wirklich vs. was erfaehrt der Charakter)
- Der Kanon-Waechter muss nach jeder Szene beide Typen extrahieren

## Alternativen (verworfen)

- **Einzelner Kanon mit Sichtbarkeitsfilter pro Charakter** → zu komplex in der Abfrage, schwer wartbar
- **Kanon nur objektiv, Charakter-Wissen implizit aus Szenen ableitbar** → zu fehleranfaellig bei nicht-linearer Entwicklung, da Szenen in beliebiger Reihenfolge geschrieben werden
