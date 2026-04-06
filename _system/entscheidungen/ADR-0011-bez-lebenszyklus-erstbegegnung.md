---
typ: entscheidung
id: ADR-0011
titel: "BEZ-Datei-Lebenszyklus – Entstehung bei Erstbegegnung"
datum: 2026-04-05
status: akzeptiert
betrifft:
  - "[[Roman_Split/_system/agenten/charakterentwickler]]"
  - "[[Roman_Split/_system/regeln/szenen-pipeline]]"
tags:
  - architektur
  - beziehung
  - pipeline
---

# ADR-0011 – BEZ-Datei-Lebenszyklus: Entstehung bei Erstbegegnung

## Kontext

Zwei Charaktere, die sich zu Beginn des Romans nicht kennen, haben keine Beziehung – eine leere BEZ-Datei würde gegen ADR-0004 (keine Redundanz bei dynamischen Daten) verstoßen. Es stellte sich die Frage, wann eine BEZ-Datei angelegt werden soll, wer das initiiert, und ob der Prozess automatisch oder halbautomatisch ablaufen soll.

Der Charakterentwickler hatte in `/szene-auswerten` bereits einen Schritt „Neue Entitäten: Falls BEZ noch nicht existiert → Angebot zur Neuanlage." Diese Formulierung war zu weich: „Angebot" suggeriert Optionalität, wo Pflicht sein sollte.

## Entscheidung

### 1. Vor der ersten Begegnung: keine BEZ-Datei

Charaktere ohne bisherige Interaktion haben kein BEZ-Dokument. In den Verknüpfungs-Abschnitten der CHAR-Dateien kann eine Vorausschau eingetragen werden (z.B. „Kommissarin – noch keine Begegnung"), aber kein eigenständiges BEZ-Dokument.

### 2. Bei der ersten Begegnung: Pflichtschritt in `/szene-auswerten`

Wenn `/szene-auswerten` in einer Szene eine Erstbegegnung zwischen zwei Entitäten erkennt (Charaktere, Charaktere mit Orten, Charaktere mit Gegenständen), ist das Anlegen einer BEZ-Datei **kein optionales Angebot, sondern ein Pflichtschritt**.

Der Agent:
1. Erkennt alle Erstbegegnungen in der Szene
2. Zeigt dem Autor die Liste: *„Folgende Erstbegegnungen habe ich erkannt: [Liste]. Ich lege BEZ-Dateien dafür an – mit dem Erstkontakt als erstem Zeitleisten-Eintrag. Soll ich fortfahren?"*
3. Wartet auf Bestätigung (kein vollautomatisches Anlegen ohne Autor-Freigabe)
4. Legt nach Bestätigung die BEZ-Datei(en) an und befüllt den Erstkontakt-Eintrag im Dialog mit dem Autor

### 3. Halbautomatisch, nicht vollautomatisch

Der Agent erkennt und schlägt vor – der Autor bestätigt. Vollautomatisches Anlegen ohne Bestätigung ist nicht erlaubt, weil:
- Räumliche Verbindungen (z.B. Johannes an einem Tatort, den die Kommissarin später untersucht) keine echte Interaktion sind und kein BEZ-Dokument auslösen sollen
- Der erste Zeitleisten-Eintrag inhaltlich bedeutsam ist (Ton der Begegnung, Machtbalance, erste Eindrücke) und im Dialog mit dem Autor entstehen soll, nicht automatisch befüllt werden darf

### 4. Sonderfall: Vorausschau in CHAR-Verknüpfungen

Wenn der Autor weiß, dass zwei Charaktere sich treffen werden, kann er im Verknüpfungs-Abschnitt der CHAR-Datei bereits einen Eintrag ohne BEZ-Link anlegen. Sobald die Szene existiert und ausgewertet wird, wird der Link nachgepflegt.

## Konsequenzen

- `/szene-auswerten` erhält eine schärfere Formulierung: „Neue Beziehungen erkennen (Pflicht)" statt „Angebot zur Neuanlage"
- Der Autor muss bei jeder Szenenauswertung aktiv bestätigen oder ablehnen, welche Erstbegegnungen BEZ-würdig sind
- Kein BEZ-Dokument ohne erste kanonische Szene als Anker
- Der Charakterentwickler wird auf v1.9 aktualisiert

## Alternativen (verworfen)

- **Vollautomatisches Anlegen ohne Bestätigung:** Zu fehleranfällig; räumliche Verbindungen würden fälschlich als Begegnungen gewertet; Erstkontakt-Eintrag wäre inhaltsleer oder falsch
- **BEZ-Datei schon vor der Begegnung anlegen (Planung):** Widerspricht ADR-0004; eine Beziehung, die noch nicht existiert, erzeugt keinen dokumentierbaren Stand
- **„Angebot" beibehalten (weiche Formulierung):** Führt dazu, dass Erstbegegnungen systematisch nicht dokumentiert werden, weil der Agent nur fragt, nicht besteht
