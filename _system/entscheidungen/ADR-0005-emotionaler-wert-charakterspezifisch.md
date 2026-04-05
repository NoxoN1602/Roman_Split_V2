---
typ: entscheidung
id: ADR-0005
titel: "Emotionaler Wert ist charakterspezifisch und dynamisch"
datum: 2026-04-04
status: akzeptiert
betrifft:
  - "[[Roman_Split/_system/templates/TEMPLATE-gegenstand]]"
  - "[[Roman_Split/_system/templates/TEMPLATE-beziehung]]"
tags:
  - architektur
  - template
  - gegenstand
  - beziehung
---

# ADR-0005 – Emotionaler Wert ist charakterspezifisch und dynamisch

## Kontext

Gegenstände in einem Roman haben neben ihrem materiellen Wert oft einen emotionalen Wert. Bei der Erstellung des Gegenstands-Templates stellte sich die Frage, ob der emotionale Wert als statisches Stammdatum im Gegenstand selbst geführt werden soll.

Beispiel: Das Pentagramm-Armband hat für Laura vor Maries Tod einen mittleren emotionalen Wert – sie findet es hübsch, aber es ist kein Identitätsobjekt. Nach Maries Tod steigt der emotionale Wert auf „identitätsstiftend", weil es das letzte Andenken an Marie ist. Gleichzeitig sieht ein Ermittler dasselbe Armband nur als Beweisstück – emotionaler Wert für ihn: gering.

## Entscheidung

Der emotionale Wert eines Gegenstands ist **kein statisches Stammdatum** im Gegenstands-Template. Er wird stattdessen in den BEZ-Dateien (Charakter ↔ Gegenstand) getrackt, weil er:

1. **Charakterspezifisch** ist – verschiedene Figuren bewerten denselben Gegenstand unterschiedlich
2. **Zeitlich veränderlich** ist – die emotionale Bedeutung kann durch Ereignisse steigen oder sinken
3. **Bereits ein System dafür existiert** – die BEZ-Datei hat szenenreferenzierte Zeitleisten für subjektive Wahrnehmung und Bedeutungsveränderung

Im Gegenstands-Template verbleibt nur der **materielle Wert** als statisches Stammdatum, da dieser objektiv und in der Regel unveränderlich ist.

Das Template enthält einen expliziten Hinweis:
> ⚠️ Der emotionale Wert ist kein statisches Stammdatum. Er ist charakterspezifisch und wird in den jeweiligen BEZ-Dateien (Charakter ↔ Gegenstand) getrackt.

## Konsequenzen

- Für jeden Charakter, der eine relevante emotionale Bindung an einen Gegenstand hat, sollte eine BEZ-Datei existieren
- Der Charakterentwickler bietet bei `/gegenstand` aktiv an, eine BEZ-Datei anzulegen
- `/szene-auswerten` erkennt emotionale Aufladungen und trägt sie in die BEZ-Dateien ein
- Es gibt keinen zentralen Überblick „Wer schätzt diesen Gegenstand wie?" – dafür muss man die BEZ-Dateien oder den Verknüpfungs-Abschnitt im Gegenstand konsultieren

## Alternativen (verworfen)

- **Statisches Feld „Wert (emotional)" in den Stammdaten:** Kann nur einen einzigen Wert abbilden – wessen emotionalen Wert? Und zu welchem Zeitpunkt? Nicht geeignet für ein System, das multiple Perspektiven und zeitliche Veränderung modelliert.
- **Liste von Charakter-Wert-Paaren im Gegenstand:** Redundant zu den BEZ-Dateien; zwei Stellen, die gepflegt werden müssen (widerspricht ADR-0004).
