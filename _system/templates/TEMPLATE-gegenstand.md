---
doc_type: gegenstand
doc_id: "GGS-"
version: "1.3"
status: entwurf # entwurf | aktiv | archiviert | gesperrt
kanon_stufe: objektiv # objektiv | subjektiv | explorativ
erstellt: "<% tp.date.now('YYYY-MM-DD') %>"
letzte_aenderung: "<% tp.date.now('YYYY-MM-DD') %>"
autor_agent: "" # z.B. charakterentwickler, manuell
gegenstand_typ: "" # schmuck | waffe | kleidung | dokument | werkzeug | moebel | fahrzeug | symbol | sonstiges
bild: "" # Pfad zur Bilddatei, z.B. "bilder/pentagramm-armband.png"
tags:
  - gegenstand
---

# Gegenstand-Kanon – [Name des Gegenstands]

> **Rolle im Roman:** [Kurzbeschreibung der Rolle]
> **Dramaturgische Funktion:** [Was leistet dieser Gegenstand für die Geschichte?]

---

## 0. BILD (KANN)

<!-- Visuelle Referenz des Gegenstands (→ ADR-0008). -->
<!-- Namenskonvention: Bild = gleicher Name wie Gegenstands-Datei, z.B. pentagramm-armband.md → bilder/pentagramm-armband.png -->
<!-- Das Bild kann manuell erstellt und in gegenstaende/bilder/ abgelegt werden. -->

![[bilder/{name}.png]]

---

## 1. ROLLE & FUNKTION (MUSS)

**Narrative Rolle:**
<!-- Wofür existiert dieser Gegenstand in der Geschichte? (z.B. Beweisstück, Erinnerungsstück, Tatwaffe, Talisman, McGuffin, Geschenk) -->

**Dramaturgische Funktion:**
<!-- Welche Aufgabe erfüllt der Gegenstand strukturell? (z.B. verbindet zwei Charaktere, treibt Handlung voran, symbolisiert Verlust, enthüllt Wahrheit) -->

**Zuordnung zu Handlungssträngen:**
<!-- Welche Plot-Linien berührt dieser Gegenstand? -->

---

## 2. OBJEKTIVE FAKTEN (MUSS)

> Diese Fakten sind kanonisch und unveränderlich, sofern nicht durch eine Kanon-Änderung mit Zeitstempel überschrieben.

### 2.1 Stammdaten

| Feld                     | Wert |
| ------------------------ | ---- |
| Bezeichnung              |      |
| Gegenstand-Typ (Schmuck, Waffe, Kleidung, Dokument, Werkzeug, Möbel, Fahrzeug, Symbol, Sonstiges) |      |
| Herkunft (woher stammt er, wer hat ihn hergestellt / gekauft / gefunden) |      |
| Wert (materiell: gering, mittel, hoch, unschätzbar, wertlos) |      |
| Einzigartigkeit (Massenware, individuell, Unikat, unersetzlich) |      |

> ⚠️ Der emotionale Wert ist kein statisches Stammdatum. Er ist charakterspezifisch (verschiedene Figuren bewerten denselben Gegenstand unterschiedlich) und kann sich über die Zeit verändern. Emotionale Bindungen werden in den jeweiligen BEZ-Dateien (Charakter ↔ Gegenstand) getrackt.

### 2.2 Physische Beschreibung

> Nur beobachtbare, objektive Details. Keine Wertungen, keine symbolischen Interpretationen.

#### Erscheinungsbild

<!-- z.B. Form, Größe, Farbe, Muster, Gravuren, Beschriftungen -->

#### Material & Beschaffenheit

<!-- z.B. Metall, Stoff, Holz, Stein, Kunststoff; Oberfläche (glatt, rau, poliert, matt) -->

#### Haptik & Gewicht

<!-- z.B. leicht, schwer, warm, kalt, scharfkantig, weich, handschmeichelnd -->

#### Zustand

| Feld                  | Wert |
| --------------------- | ---- |
| Allgemeinzustand (neu, gepflegt, getragen, abgenutzt, beschädigt, zerstört) |      |
| Gebrauchsspuren (keine, leicht, deutlich, stark, patiniert) |      |
| Besondere Merkmale (Kratzer, Gravur, Flecken, Reparaturspuren, Rost, Verfärbungen) |      |

---

## 3. HERKUNFT & GESCHICHTE (MUSS)

> Woher kommt dieser Gegenstand? Welche Geschichte trägt er mit sich?

**Entstehung / Erwerb:**
<!-- Wann und wie ist der Gegenstand in die Geschichte gekommen? Gekauft, geschenkt, geerbt, gefunden, gestohlen? -->

**Vorbesitzer:**
<!-- Gab es relevante frühere Besitzer? Wenn ja, welche Bedeutung hatte der Gegenstand für sie? -->

**Bekannte Geschichte vor Romanbeginn:**
<!-- Was ist mit dem Gegenstand passiert, bevor die Handlung einsetzt? -->

---

## 4. BESITZ- & STANDORT-TRACKING (MUSS)

> Wo befindet sich der Gegenstand zu welchem Zeitpunkt? Wer besitzt ihn? Jede Veränderung wird szenenreferenziert. Der aktuelle Besitzer und Standort ergibt sich immer aus dem letzten Eintrag.

### Initialstatus (vor Romanbeginn)

| Feld | Wert |
| ---- | ---- |
| Besitzer |      |
| Standort |      |

### Veränderungen

| Ab Szene / Romanzeit | Veränderung | Neuer Besitzer | Neuer Standort |
| --------------------- | ----------- | -------------- | -------------- |
|                       |             |                |                |

---

## 5. SZENENREFERENZIERTE ZUSTANDSVERÄNDERUNGEN (MUSS)

> Wie verändert sich der physische Zustand des Gegenstands im Verlauf des Romans?

| Ab Szene / Romanzeit | Veränderung | Neuer Zustand |
| --------------------- | ----------- | ------------- |
|                       |             |               |

---

## 6. GRENZEN & VERBOTE (MUSS)

> Was darf mit diesem Gegenstand NICHT passieren? Bindend für alle Agenten.

<!-- z.B. "Darf nicht zerstört werden (wird am Ende als Beweisstück gebraucht)" -->
<!-- z.B. "Darf nicht von Charakter X gefunden werden (erst in Akt 3)" -->
<!-- z.B. "Keine übernatürlichen Eigenschaften (realistisches Setting)" -->

---

## 7. SYMBOLIK & BEDEUTUNGSEBENE (KANN)

**Symbolische Bedeutung:**
<!-- z.B. steht für Erinnerung, Verbindung, Verlust, Macht, Schuld, Hoffnung, Identität -->

**Bedeutungsveränderung im Romanverlauf:**
<!-- Verändert sich die symbolische Aufladung? z.B. vom harmlosen Schmuckstück zum letzten Andenken an eine Tote -->

**Wissen der Figuren über die Bedeutung:**
<!-- Wer weiß um die Bedeutung? Wer ahnt nichts davon? Gibt es unterschiedliche Bedeutungsschichten? -->

---

## 8. BEKANNTE EREIGNISSE (KANN)

> Szenen, in denen dieser Gegenstand eine Rolle spielt. Wird fortlaufend ergänzt.

| Szene | Kurzbeschreibung | Auswirkung auf den Gegenstand |
| ----- | ---------------- | ----------------------------- |
|       |                  |                               |

---

## 9. STATUS & OFFENES

**Was ist noch unklar?**

**Was darf sich später ändern?**

**Was ist festgesetzt?**

---

## 10. VERKNÜPFUNGEN (KONSOLIDIERT)

> Alle Querverweise gesammelt für Obsidian Graph View und Dataview. Wird von Agenten gepflegt.

### Charaktere

| Charakter | Beziehung zum Gegenstand | Dokument |
| --------- | ------------------------ | -------- |
|           |                          |          |

### Orte

| Ort | Standort / Bedeutung | Dokument |
| --- | -------------------- | -------- |
|     |                      |          |

### Andere Gegenstände

| Gegenstand | Beziehung (z.B. Teil eines Sets, Gegenstück, Schlüssel/Schloss) | Dokument |
| ---------- | --------------------------------------------------------------- | -------- |
|            |                                                                 |          |

### Beziehungen

| Beziehung | Relevanz | Dokument |
| --------- | -------- | -------- |
|           |          |          |

### Plot-Stränge

| Strang | Rolle des Gegenstands im Strang | Dokument |
| ------ | ------------------------------- | -------- |
|        |                                 |          |

### Szenen

| Szene | Funktion des Gegenstands in der Szene | Dokument |
| ----- | ------------------------------------- | -------- |
|       |                                       |          |

---

<!-- ENDE DES GEGENSTANDS-TEMPLATES -->
