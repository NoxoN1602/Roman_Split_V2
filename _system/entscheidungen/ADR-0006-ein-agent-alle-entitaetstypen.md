---
typ: entscheidung
id: ADR-0006
titel: "Ein Agent für alle Entitätstypen"
datum: 2026-04-04
status: akzeptiert
betrifft:
  - "[[charakterentwickler]]"
tags:
  - architektur
  - agent
---

# ADR-0006 – Ein Agent für alle Entitätstypen

## Kontext

Das Roman-Autorensystem arbeitet mit vier Entitätstypen: Charaktere, Orte, Gegenstände und Beziehungen. Alle vier folgen einem ähnlichen Lebenszyklus: Erstellen (Drei-Phasen-Workflow), Erweitern (Abschnitt für Abschnitt), Auswerten (nach Szenen) und Prüfen (Vollständigkeit und Konsistenz). Es stellte sich die Frage, ob jeder Entitätstyp einen eigenen Agenten braucht oder ob ein einziger Agent alle Typen verwalten kann.

## Entscheidung

Der **Charakterentwickler** ist der einzige Agent für alle vier Entitätstypen. Orte, Gegenstände und Beziehungen sind keine sekundäre Zuständigkeit mehr, sondern primär.

**Begründung:**
1. **Gleicher Workflow:** Alle Entitätstypen folgen demselben Drei-Phasen-Muster (Freies Erzählen → Entwurf auf Template mappen → optionale Vertiefung). Die Vorgehensweise ist identisch, nur die Fragen und Abschnitte unterscheiden sich.
2. **Kontextuelle Nähe:** Die meisten Orte und Gegenstände entstehen im Kontext eines Charakters – Lauras Zimmer, Maries Armband. Ein separater Agent müsste trotzdem den Charakter-Kontext laden.
3. **Weniger Agenten-Wechsel:** Der Autor muss nicht zwischen drei Agenten hin- und herwechseln, wenn er einen Charakter, seinen Wohnort und seinen wichtigsten Gegenstand in einer Session anlegen will.
4. **Einheitliche Szenen-Auswertung:** `/szene-auswerten` muss ohnehin Veränderungen an allen Typen gleichzeitig erkennen. Ein Agent, der alle Typen kennt, kann das in einem Durchgang.

Der Agent heißt weiterhin „Charakterentwickler" (nicht „Entitätsentwickler"), weil Charaktere der häufigste und komplexeste Entitätstyp bleiben und der Name intuitiver ist.

## Konsequenzen

- Der Charakterentwickler hat eine größere Agenten-Definition (v1.5: 13 Slash-Befehle)
- Alle `/ort`-, `/gegenstand`-, `/beziehung`- und `/check`-Befehle laufen über denselben Agenten
- Es gibt keinen spezialisierten „Ort-Experten" – der Charakterentwickler muss die gleiche Tiefe bei Ortsbeschreibungen erreichen wie bei Charakterpsychologie
- Die Agenten-Definition ist das zentrale Dokument für den gesamten Entitäts-Workflow und muss sorgfältig gepflegt werden

## Alternativen (verworfen)

- **Separate Agenten pro Entitätstyp (Ort-Entwickler, Gegenstands-Entwickler):** Zu viel Overhead; gleicher Workflow, nur andere Fragen. Würde zu Agenten-Wechseln mitten in der Arbeit führen.
- **Ein generischer „Entitäts-Entwickler" statt „Charakterentwickler":** Semantisch korrekt, aber weniger intuitiv. „Ich will einen Charakter erstellen" → `/neuer-charakter` ist natürlicher als `/neue-entitaet charakter`.
- **Orte und Gegenstände nur als Nebenprodukt der Charaktererstellung:** Zu einschränkend. Es gibt Orte (Tatort) und Gegenstände (Tatwaffe), die nicht primär einem Charakter „gehören", aber trotzdem dokumentiert werden müssen.
