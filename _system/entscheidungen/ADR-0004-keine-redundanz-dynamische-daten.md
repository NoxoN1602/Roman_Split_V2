---
typ: entscheidung
id: ADR-0004
titel: "Keine Redundanz bei dynamischen Daten"
datum: 2026-04-04
status: akzeptiert
betrifft:
  - "[[Roman_Split/_system/templates/TEMPLATE-charakter]]"
  - "[[Roman_Split/_system/templates/TEMPLATE-beziehung]]"
  - "[[Roman_Split/_system/templates/TEMPLATE-ort]]"
  - "[[Roman_Split/_system/templates/TEMPLATE-gegenstand]]"
tags:
  - architektur
  - template
  - kanon
---

# ADR-0004 – Keine Redundanz bei dynamischen Daten

## Kontext

In einem nicht-linear geschriebenen Roman verändern sich Zustände ständig: Beziehungen entwickeln sich, Gegenstände wechseln den Besitzer, Orte werden umgebaut, Charaktere altern. Wenn ein Template sowohl eine szenenreferenzierte Zeitleiste als auch ein separates Feld „Aktueller Stand" führt, müssen bei jeder Änderung zwei Stellen gepflegt werden. Bei nicht-linearem Schreiben – wo Szenen in beliebiger Reihenfolge entstehen – ist das besonders fehleranfällig, da der „aktuelle Stand" von der Romanzeit abhängt und nicht vom Erstellungszeitpunkt der Szene.

## Entscheidung

Kein Template hat einen separaten „Aktueller Stand"-Block für dynamische Daten. Der aktuelle Stand ergibt sich immer aus dem letzten Eintrag in den szenenreferenzierten Zeitleisten.

Dies gilt für:
- **Beziehungen:** Kein „Aktueller Beziehungsstatus" – letzter Eintrag in der objektiven Zeitleiste (Abschnitt 2) ist der aktuelle Status
- **Gegenstände:** Kein „Aktueller Besitzer" oder „Aktueller Standort" in den Stammdaten – letzter Eintrag im Besitz-/Standort-Tracking (Abschnitt 4) ist maßgeblich
- **Orte:** Kein „Aktuelle Beschreibung" – Initialstatus + alle Veränderungen (Abschnitt 5) ergeben den aktuellen Zustand
- **Charaktere:** Kein „Aktueller psychologischer Zustand" – Initialstatus + Entwicklungsbogen (Abschnitt 8) ergeben den aktuellen Stand

Statische Daten (z.B. Geburtstag, Herkunft eines Gegenstands, geographische Lage eines Orts) bleiben in den Stammdaten, da sie sich nicht ändern.

## Konsequenzen

- Keine Widersprüche zwischen Zeitleiste und „Aktuellem Stand"
- Agenten müssen die Zeitleiste lesen und den letzten Eintrag als aktuellen Stand interpretieren
- Bei sehr langen Zeitleisten kann es für den Ghostwriter aufwändig sein, den aktuellen Stand zu ermitteln – hier hilft `/check`, das Lücken und Inkonsistenzen aufdeckt
- Nicht-lineares Schreiben wird unterstützt: Ein Eintrag in der Zeitleiste mit Romanzeit RT2025-03-15 ist „aktueller" als einer mit RT2025-01-10, unabhängig davon, wann sie geschrieben wurden

## Alternativen (verworfen)

- **Separates Feld „Aktueller Stand" + Zeitleiste:** Redundanz erzeugt Widerspruchsrisiko; bei nicht-linearer Entwicklung unklar, welcher Stand „aktuell" ist
- **Nur „Aktueller Stand" ohne Zeitleiste:** Verliert die Historie; bei Retcon-Situationen nicht rekonstruierbar, wann sich etwas geändert hat
