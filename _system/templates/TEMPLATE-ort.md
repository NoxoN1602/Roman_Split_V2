---
doc_type: ort
doc_id: "ORT-"
version: "1.3"
status: entwurf # entwurf | aktiv | archiviert | gesperrt
kanon_stufe: objektiv # objektiv | subjektiv | explorativ
erstellt: "<% tp.date.now('YYYY-MM-DD') %>"
letzte_aenderung: "<% tp.date.now('YYYY-MM-DD') %>"
autor_agent: "" # z.B. charakterentwickler, manuell
ort_typ: "" # innenraum | aussenraum | gebaeude | landschaft | fahrzeug | oeffentlich | virtuell
grundriss: "" # Pfad zur .drawio-Quelldatei, z.B. "grundrisse/lauras-zimmer.drawio"
tags:
  - ort
---

# Ort-Kanon – [Name des Orts]

> **Rolle im Roman:** [Kurzbeschreibung der Rolle]
> **Dramaturgische Funktion:** [Was leistet dieser Ort für die Geschichte?]

---

## 0. GRUNDRISS (KANN)

<!-- Grundriss-Anzeige (→ ADR-0008). Doppeldatei-Ansatz: -->
<!-- Quelle (editierbar): grundrisse/{name}.drawio – bearbeiten in draw.io Desktop -->
<!-- Anzeige (SVG-Export): grundrisse/{name}.drawio.svg – draw.io erzeugt diese Endung automatisch -->
<!-- Namenskonvention: Grundriss = gleicher Name wie Ort-Datei -->
<!-- Workflow: .drawio in draw.io öffnen → Exportieren als SVG → .drawio.svg wird erzeugt -->

![[grundrisse/{name}.drawio.svg]]

---

## 1. ROLLE & FUNKTION (MUSS)

**Narrative Rolle:**
<!-- Wofür existiert dieser Ort in der Geschichte? (z.B. Rückzugsort, Tatort, Treffpunkt, Arbeitsplatz, Symbolort) -->

**Dramaturgische Funktion:**
<!-- Welche Aufgabe erfüllt der Ort strukturell? (z.B. charakterisiert eine Figur indirekt, erzeugt Atmosphäre, ermöglicht Konfrontation, isoliert Figuren) -->

**Zuordnung zu Handlungssträngen:**
<!-- Welche Plot-Linien berührt dieser Ort? -->

---

## 2. OBJEKTIVE FAKTEN (MUSS)

> Diese Fakten sind kanonisch und unveränderlich, sofern nicht durch eine Kanon-Änderung mit Zeitstempel überschrieben.

### 2.1 Stammdaten

| Feld                     | Wert |
| ------------------------ | ---- |
| Bezeichnung              |      |
| Ort-Typ (Innenraum, Außenraum, Gebäude, Landschaft, Fahrzeug, Öffentlich, Virtuell) |      |
| Übergeordneter Ort (→ ORT-Referenz, z.B. das Gebäude, in dem ein Raum liegt) |      |
| Untergeordnete Orte (→ ORT-Referenzen, z.B. Räume innerhalb eines Gebäudes) |      |
| Geographische Lage (Stadt, Stadtteil, Straße, GPS – soweit relevant) |      |
| Zugang (öffentlich, privat, eingeschränkt, geheim) |      |
| Besitzer / Bewohner (→ CHAR-Referenz) |      |

### 2.2 Physische Beschreibung

> Nur beobachtbare, objektive Details. Keine Wertungen, keine atmosphärischen Interpretationen.

#### Raumstruktur / Topografie

<!-- z.B. Grundriss, Stockwerk, Fläche, Raumaufteilung, Zonen, Gelände, Vegetation -->

#### Materialien & Oberflächen

<!-- z.B. Boden (Parkett, Beton, Erde), Wände (Putz, Holz, Glas), Decke, natürliche Materialien -->

#### Einrichtung & Gegenstände

<!-- Möbel, Geräte, Dekorationsgegenstände – gegliedert nach Zonen, wenn sinnvoll -->
<!-- Verweise auf GGS-Dokumente, wenn ein Gegenstand eigenständig kanonisch relevant ist -->

#### Licht & Beleuchtung

<!-- Natürliches Licht (Fenster, Anzahl, Ausrichtung), künstliches Licht (Lampentypen, Lichtfarbe) -->

#### Zustand & Pflege

| Feld                  | Wert |
| --------------------- | ---- |
| Allgemeinzustand (neu, gepflegt, abgenutzt, verfallen, verwüstet) |      |
| Sauberkeit (steril, sauber, bewohnt, unordentlich, verdreckt) |      |
| Alter / Bauepoche     |      |

---

## 3. SENSORISCHE SIGNATUR (MUSS)

> Was nimmt man mit den Sinnen wahr, wenn man diesen Ort betritt? Objektiv beschrieben, nicht interpretiert.

| Sinn      | Beschreibung |
| --------- | ------------ |
| Geräusche | <!-- z.B. Stille, Straßenlärm, Vogelgezwitscher, Brummen einer Heizung, Knarren --> |
| Gerüche   | <!-- z.B. Holz, Staub, Essen, Parfüm, Feuchtigkeit, frische Luft --> |
| Temperatur / Luft | <!-- z.B. warm, zugig, stickig, kühl, feucht, trocken --> |
| Haptik    | <!-- z.B. weiche Teppiche, kalter Stein, raues Holz – was man berührt --> |

---

## 4. ATMOSPHÄRE & WIRKUNG (MUSS)

> Wie wirkt dieser Ort auf Menschen, die ihn betreten? Dies ist eine interpretative Ebene, die über die rein sensorische Beschreibung hinausgeht.

**Grundatmosphäre:**
<!-- z.B. gemütlich, bedrohlich, steril, chaotisch, geheimnisvoll, einladend, beklemmend -->

**Emotionale Wirkung:**
<!-- z.B. vermittelt Sicherheit, erzeugt Unbehagen, weckt Nostalgie, isoliert -->

**Was dieser Ort über seinen Bewohner / Nutzer verrät:**
<!-- z.B. Kontrollbedürfnis, Vernachlässigung, Geborgenheit, sozialer Status -->

---

## 5. SZENENREFERENZIERTE VERÄNDERUNGEN (MUSS)

> Wie verändert sich der Ort im Verlauf des Romans? Jede Veränderung wird mit der verursachenden Szene verknüpft.

### Initialstatus (vor Romanbeginn)

<!-- Wie sieht der Ort aus, bevor die Handlung einsetzt? Kurze Zusammenfassung des Ausgangszustands. -->

### Veränderungen

| Ab Szene / Romanzeit | Veränderung | Neuer Zustand |
| --------------------- | ----------- | ------------- |
|                       |             |               |

---

## 6. GRENZEN & VERBOTE (MUSS)

> Was darf an diesem Ort NICHT passieren oder existieren? Bindend für alle Agenten.

<!-- z.B. "Kein direktes Sonnenlicht möglich (Dachboden mit nur zwei kleinen Fenstern)" -->
<!-- z.B. "Keine lauten Geräusche von außen (abgelegene Lage)" -->
<!-- z.B. "Keine moderne Technik (Ort spielt in historischem Setting)" -->

---

## 7. BEKANNTE EREIGNISSE (KANN)

> Szenen, die an diesem Ort stattfinden oder stattgefunden haben. Wird fortlaufend ergänzt.

| Szene | Kurzbeschreibung | Auswirkung auf den Ort |
| ----- | ---------------- | ---------------------- |
|       |                  |                        |

---

## 8. SYMBOLIK & MOTIVE (KANN)

**Symbolische Bedeutung des Orts:**
<!-- z.B. steht für Kindheit, Kontrolle, Freiheit, Gefangenschaft, Übergang -->

**Wiederkehrende Bilder / Motive:**
<!-- z.B. Licht und Schatten, Enge und Weite, Ordnung und Chaos -->

**Kontraste zu anderen Orten:**
<!-- z.B. "Kontrastiert mit ORT-xyz durch ..." → ORT-Referenz -->

---

## 9. STATUS & OFFENES

**Was ist noch unklar?**

**Was darf sich später ändern?**

**Was ist festgesetzt?**

---

## 10. VERKNÜPFUNGEN (KONSOLIDIERT)

> Alle Querverweise gesammelt für Obsidian Graph View und Dataview. Wird von Agenten gepflegt.

### Charaktere

| Charakter | Beziehung zum Ort | Dokument |
| --------- | ------------------ | -------- |
|           |                    |          |

### Übergeordnete / Untergeordnete Orte

| Ort | Beziehung | Dokument |
| --- | --------- | -------- |
|     |           |          |

### Gegenstände

| Gegenstand | Standort / Bedeutung | Dokument |
| ---------- | -------------------- | -------- |
|            |                      |          |

### Beziehungen

| Beziehung | Relevanz | Dokument |
| --------- | -------- | -------- |
|           |          |          |

### Plot-Stränge

| Strang | Rolle des Orts im Strang | Dokument |
| ------ | ------------------------ | -------- |
|        |                          |          |

### Szenen

| Szene | Funktion des Orts in der Szene | Dokument |
| ----- | ------------------------------ | -------- |
|       |                                |          |

---

<!-- ENDE DES ORT-TEMPLATES -->
