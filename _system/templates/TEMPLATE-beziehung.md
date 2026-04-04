---
doc_type: beziehung
doc_id: "BEZ-"
beziehungstyp: "" # charakter-charakter | charakter-gegenstand | charakter-ort
version: "1.1"
status: entwurf # entwurf | aktiv | archiviert
kanon_stufe: objektiv
erstellt: "<% tp.date.now('YYYY-MM-DD') %>"
letzte_aenderung: "<% tp.date.now('YYYY-MM-DD') %>"
autor_agent: ""
entitaet_a: "" # CHAR-Referenz (immer ein Charakter)
entitaet_b: "" # CHAR-, GGS- oder ORT-Referenz
tags:
  - beziehung
---

# Beziehung – [Entität A] ↔ [Entität B]

> **Beziehungstyp:** [charakter-charakter | charakter-gegenstand | charakter-ort]
> **Kurzcharakterisierung:** [Ein Satz, der die Beziehung auf den Punkt bringt]

---

## 1. GRUNDDATEN (MUSS)

| Feld              | Wert |
| ----------------- | ---- |
| Typ               | <!-- enge Freundschaft, Eltern-Kind, Rivalität, romantisch, Mentor-Schüler, Besitz, emotionale Bindung, Zufluchtsort, ... --> |
| Ursprung          | <!-- Wie und wann ist die Beziehung entstanden? --> |
| Machtverhältnis   | <!-- symmetrisch, asymmetrisch, wechselnd --> |
| Dynamik           | <!-- Kurzbeschreibung der funktionalen Dynamik --> |

---

## 2. OBJEKTIVER BEZIEHUNGSSTATUS (MUSS)

> Kanonische Fakten über die Beziehung, wie sie ein allwissender Erzähler beschreiben würde. Szenenreferenziert – jede Veränderung wird mit der verursachenden Szene verknüpft.

### Initialstatus (vor Romanbeginn)

<!-- Wie sieht die Beziehung objektiv aus, bevor die Handlung einsetzt? -->

### Szenenreferenzierte Veränderungen

| Ab Szene / Romanzeit | Veränderung | Neuer objektiver Status |
| --------------------- | ----------- | ----------------------- |
|                       |             |                         |

---

## 3. SUBJEKTIVE SICHT (MUSS)

> Wie nehmen die Beteiligten die Beziehung wahr? Diese Sichten können voneinander und vom objektiven Status abweichen.

### Perspektive: [Entität A – Name]

#### Initialstatus (vor Romanbeginn)

<!-- Wie empfindet dieser Charakter die Beziehung? Was projiziert er hinein? Was leugnet er? -->

#### Szenenreferenzierte Veränderungen

| Ab Szene / Romanzeit | Was verändert sich in der Wahrnehmung? |
| --------------------- | -------------------------------------- |
|                       |                                        |

---

### Perspektive: [Entität B – Name]

> ⚠️ Bei charakter-gegenstand und charakter-ort entfällt dieser Block (Gegenstände und Orte haben keine Perspektive). Stattdessen kann hier die **Funktion des Gegenstands/Orts für den Charakter** vertieft werden.

#### Initialstatus (vor Romanbeginn)

<!-- Wie empfindet dieser Charakter die Beziehung? (Bzw. bei Gegenstand/Ort: Welche Funktion erfüllt er für den Charakter?) -->

#### Szenenreferenzierte Veränderungen

| Ab Szene / Romanzeit | Was verändert sich in der Wahrnehmung? |
| --------------------- | -------------------------------------- |
|                       |                                        |

---

## 4. ZENTRALE BEZIEHUNGSDYNAMIK (MUSS)

> Die Mechanismen, die diese Beziehung antreiben und am Leben halten.

<!-- z.B.:
- Nähe ohne explizite Aussprachen
- Unterschiedliche Nähebedürfnisse
- Stabilität durch Gewohnheit vs. bewusste Pflege
- Konfliktvermeidung auf beiden Seiten
- Gegenseitige Ergänzung vs. Reibung
-->

---

## 5. LATENTE KONFLIKTLINIEN (MUSS)

> Konflikte, die unter der Oberfläche liegen und jederzeit aktiviert werden könnten.

<!-- z.B.:
- Autonomie vs. Bindung
- Schutz vs. Bevormundung
- Ungleichgewicht im sozialen Risiko
- Unterschiedliche Strategien im Umgang mit Unsicherheit
-->

---

## 6. SYMBOLISCHE EBENE (KANN)

### Gemeinsame Rituale

<!-- Wiederkehrende Handlungen, Gewohnheiten, ungeschriebene Regeln -->

### Gegenstände mit emotionalem Wert

<!-- Objekte, die in der Beziehung eine Rolle spielen (→ GGS-Referenzen) -->

### Orte

<!-- Orte, die mit der Beziehung verbunden sind (→ ORT-Referenzen) -->
<!-- z.B. Terrain von A vs. Terrain von B, gemeinsame Orte, vermiedene Orte -->

---

## 7. WENDEPUNKTE & BRUCHSTELLEN (KANN)

> Momente, die die Beziehung grundlegend verändert haben oder verändern könnten.

### Bereits eingetretene Wendepunkte

| Romanzeit / Szene | Wendepunkt | Auswirkung auf die Beziehung |
| ------------------ | ---------- | ---------------------------- |
|                    |            |                              |

### Potenzielle Bruchstellen (explorativ)

<!-- Was könnte die Beziehung zerstören oder fundamental verändern? -->

---

## 8. BEKANNTE EREIGNISSE (KANN)

> Szenen, in denen diese Beziehung eine Rolle spielt. Wird fortlaufend ergänzt.

| Szene | Kurzbeschreibung | Auswirkung auf die Beziehung |
| ----- | ---------------- | ---------------------------- |
|       |                  |                              |

---

## 9. STATUS & OFFENES

**Was ist noch unklar?**

**Was darf sich später ändern?**

**Was ist festgesetzt?**

---

## 10. VERKNÜPFUNGEN

### Dokumente

| Dokument | Typ | Relevanz |
| -------- | --- | -------- |
|          |     |          |

### Szenen mit dieser Beziehung

| Szene | Funktion der Beziehung in der Szene |
| ----- | ------------------------------------ |
|       |                                      |

---

<!-- ENDE DES BEZIEHUNGS-TEMPLATES -->
