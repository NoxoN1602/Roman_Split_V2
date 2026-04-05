# Changelog

## 2026-04-05 – v2.1
- **Neu:** [[Roman_Split/_system/entscheidungen/ADR-0010-obsidian-wiki-links-standard-verlinkung]] – Obsidian-Wiki-Links als Standard für alle internen Verlinkungen
- **Aktualisiert:** Alle Systemdokumente (ADR-0001–0009, Agenten, Regeln, Plot-Dateien, claude.md, commands.md) auf neues Link-Format umgestellt
- **Aktualisiert:** [[Roman_Split/_system/regeln/naming-conventions]] v2.1 – Verweise-Tabelle auf neues Format aktualisiert, ADR-0010 ergänzt

## 2026-04-04 – v2.0
- **Neu:** [[Roman_Split/_system/entscheidungen/ADR-0009-plotentwicklung-agenten-und-workflow]] – Plotentwicklung: 6 neue Agenten, 5-Stufen-Workflow, Kreativ/Pruef-Trennung, Methoden-Referenzsystem
- **Neu:** [[Roman_Split/_system/agenten/plotarchitect]] v1.0 – Kreativagent fuer Plotentwicklung (5-Stufen-Workflow, Methoden-Beratung, Agenten-Bewusstsein)
- **Neu:** [[Roman_Split/_system/agenten/plotanalyst]] v1.0 – Pruefagent fuer Strukturanalyse gegen Dramaturgiemodell
- **Neu:** [[Roman_Split/_system/agenten/conflictanalyst]] v1.0 – Pruefagent fuer Spannungs-/Konfliktanalyse
- **Neu:** [[Roman_Split/_system/agenten/canonguardian]] v1.0 – Pruefagent fuer Kanon-Konsistenz (Plot, Szenenvertraege, Szenen)
- **Neu:** [[Roman_Split/_system/agenten/sceneideationpartner]] v1.0 – Kreativagent fuer Szenen-Aufloesung und Szenenvertraege
- **Neu:** Verzeichnis `_system/referenz/` – Dramaturgiemodelle
- **Neu:** [[Roman_Split/_system/referenz/REF-save-the-cat]] – Save the Cat Beat Sheet (15 Beats)
- **Neu:** [[Roman_Split/_system/referenz/REF-drei-akt]] – Drei-Akt-Struktur
- **Neu:** [[Roman_Split/_system/referenz/REF-heldenreise]] – Heldenreise (Campbell/Vogler, 12 Stufen)
- **Neu:** [[Roman_Split/_system/referenz/REF-story-circle]] – Dan Harmons Story Circle (8 Schritte)
- **Neu:** [[Roman_Split/_system/templates/TEMPLATE-plot]] – Template fuer Plot-Dokumente
- **Neu:** [[Roman_Split/_system/templates/TEMPLATE-plot-working]] – Template fuer Arbeitszustand
- **Aktualisiert:** [[Roman_Split/commands]] – `/plot` und `/plot-check` hinzugefuegt (12 Befehle gesamt)
- **Aktualisiert:** [[Roman_Split/claude]] – Neue Abschnitte: Agenten-System, Plot-System, erweiterte ADR-Tabelle

## 2026-04-03 – v1.5
- **Neu:** [[Roman_Split/_system/regeln/szenen-lebenszyklus]] – Regel fuer Szenen-Status (entwurf → abgenommen → revision → archiviert)
- **Neu:** [[Roman_Split/_system/regeln/szenen-pipeline]] – Pipeline-Regel nach Szenen-Abnahme (Kontinuitaet → Charakter-Auswertung → Kanon-Ableitung)
- **Aktualisiert:** [[Roman_Split/_system/agenten/charakterentwickler]] v1.1 – Neuer Slash-Befehl `/szene-auswerten`, Leserechte fuer `szenen/`, Abschnitt "Automatische Trigger", `/check` um Szenen-Abdeckung erweitert

## 2026-04-03 – v1.4
- **Neu:** [[Roman_Split/_system/agenten/charakterentwickler]] – Agenten-Definition mit 9 Slash-Befehlen, Phasen-Logik, Dateizugriff und Zusammenspiel

## 2026-04-03 – v1.3
- **Korrektur:** [[Roman_Split/_system/templates/TEMPLATE-charakter]] – Dateiname von TEMPLATE_charakter auf TEMPLATE-charakter (ADR-0003-konform)
- **Aktualisiert:** [[Roman_Split/_system/templates/TEMPLATE-charakter]] – Frontmatter gestrafft (nur Systemfelder), Templater-Syntax fuer Datumsfelder, Beispielwerte in Klammern bei allen Tabellenfeldern
- **Aktualisiert:** [[Roman_Split/_system/regeln/naming-conventions]] v2.1 – Template-Muster auf Bindestrich korrigiert
- **Aktualisiert:** [[Roman_Split/_system/entscheidungen/ADR-0003-einheitliche-prefixe-und-dateinamen]] – Template-Zeile korrigiert

## 2026-04-03 – v1.2
- **Neu:** [[Roman_Split/_system/entscheidungen/ADR-0003-einheitliche-prefixe-und-dateinamen]] – Standardisierte Prefixe, Kleinschreibung, Bindestrich-Konvention
- **Aktualisiert:** [[Roman_Split/_system/regeln/naming-conventions]] v2.0 – Vollstaendige Prefix-Tabelle inkl. Templates, Agenten, Regeln; Migrationshinweis; Verweisformate
- **Neu:** [[Roman_Split/_system/templates/TEMPLATE-charakter]] – Fusioniertes Charakter-Template (15 Abschnitte, MUSS/KANN-Logik, Frontmatter)

## 2026-04-03 – v1.1
- **Ergaenzt:** Konzept- und Entscheidungsdokumentation ([[Roman_Split/_system/konzept/KON-0001-systemkonzept]] v1.1)
- **Neu:** [[Roman_Split/_system/entscheidungen/ADR-0001-kanon-objektiv-subjektiv]] – Kanon getrennt in objektiv und subjektiv
- **Neu:** [[Roman_Split/_system/entscheidungen/ADR-0002-keine-umlaute-dateinamen]] – ASCII-only Dateinamen
- **Neu:** Verzeichnisse `_system/konzept/` und `_system/entscheidungen/`

## 2026-04-03 – v1.0
- **Initial:** Systemkonzept erstellt ([[Roman_Split/_system/konzept/KON-0001-systemkonzept]] v1.0)
- Verzeichnisstruktur definiert
- Frontmatter-Standards fuer alle Dateitypen
- Kanon-System mit Zeitstempeln und Verbindlichkeitsstufen
- 6 Agenten definiert (Plot-Architekt, Charakter-Entwickler, Beziehungs-Manager, Ghostwriter, Kanon-Waechter, Kontinuitaets-Pruefer)
- Workflow fuer nicht-lineare Szenen-Erstellung
