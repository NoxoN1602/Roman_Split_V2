---
typ: regel
id: REG-kanon
titel: "Kanon-Regeln"
status: aktiv
tags:
  - regel
  - kanon
---

# Kanon-Regeln

## Grundsaetze

1. **Kanon ist bindend.** Kein Agent darf kanonische Fakten ignorieren oder widerspruechlich schreiben.
2. **Zeitgestempelt.** Jeder Kanon-Eintrag hat `gueltig_ab` und optional `gueltig_bis` in Romanzeit.
3. **Objektiv vs. Subjektiv.** Siehe [[Roman_Split/_system/entscheidungen/ADR-0001-kanon-objektiv-subjektiv]].
4. **Ueberschreibung.** Ein neuerer Kanon-Eintrag mit gleichem Thema ueberschreibt aeltere Eintraege im ueberlappenden Gueltigkeitszeitraum.
5. **Automatische Erzeugung.** Nach jeder finalisierten Szene erzeugt der Kanon-Waechter neue Kanon-Eintraege.
6. **Konflikterkennung.** Vor dem Schreiben einer Szene prueft der Kontinuitaets-Pruefer alle relevanten Kanon-Eintraege.

## Verbindlichkeitsstufen

| Stufe | Bedeutung | Aenderbar? |
|---|---|---|
| `absolut` | Unveraenderlich – Naturgesetze, Magie-Regeln, historische Fixen | Nein |
| `stark` | So war es – Aenderung nur mit expliziter Begruendung und Autor-Genehmigung | Nur mit ADR |
| `weich` | Wahrscheinlich so – kann bei Bedarf angepasst werden | Ja, mit Dokumentation |

## Kanon-Abfrage-Logik

Fuer eine Szene mit `romanzeit_start = T`:

1. **Objektiver Kanon:** Alle Eintraege mit `gueltig_ab <= T` UND (`gueltig_bis > T` ODER `gueltig_bis = null`)
2. **Subjektiver Kanon:** Fuer jeden beteiligten Charakter, gleiche Zeitlogik
3. **Ortskanon:** Alle Eintraege die den Szenenort betreffen
4. **Gegenstandskanon:** Alle Eintraege die beteiligte Gegenstaende betreffen

## Retcon (Retroactive Continuity)

Wenn eine neu geschriebene Szene zeitlich VOR bestehenden Szenen spielt und neuen Kanon einfuehrt, der bestehende Szenen beruehrt:

1. Kanon-Waechter prueft Kompatibilitaet mit spaeterem Kanon
2. Bei Widerspruch: Retcon-Eintrag erstellen
3. Betroffene Szenen markieren als `status: revision-noetig`
4. Autor entscheidet: Neue Szene anpassen ODER bestehende Szenen revidieren

## Kanon-Erzeugung nach Szene

Der Kanon-Waechter extrahiert aus jeder finalisierten Szene:

- **Was passiert?** → Objektiver Kanon
- **Was erfaehrt welcher Charakter?** → Subjektiver Kanon pro Charakter
- **Welche Gegenstaende wechseln den Besitzer?** → Objektiver Kanon + Gegenstand-Update
- **Welche Beziehungen veraendern sich?** → Beziehungsdokument-Update + Kanon
- **Welche Orte veraendern sich?** → Ortsdokument-Update + Kanon
